# Resume Formatting Fixes - Detailed Report

## Problem Identified
The EN2 resume had a formatting issue in the Education section where the University of Michigan-Shanghai Jiao Tong University entry had too much text on one line with the date, causing the line to break awkwardly.

### Before (EN2 - Lines 87-90):
```tex
\textbf{University of Illinois Urbana-Champaign}\hfill Champaign, Illinois\\
Bachelor of Science in Statistics, Mathematics Minor; GPA: 3.93/4.00\hfill January 2023 -- May 2025\\[-1pt]
\textbf{University of Michigan--Shanghai Jiao Tong University Joint Institute}\hfill Shanghai, China\\
Coursework toward a B.E. in Mechanical Engineering; transferred to UIUC; First Class Scholarship\hfill September 2019 -- December 2020
```

**Issue**: The date "September 2019 -- December 2020" was forced to wrap because the description text was too long.

### After (EN2 - Lines 87-91):
```tex
\textbf{University of Illinois Urbana-Champaign}\hfill Champaign, Illinois\\
Bachelor of Science in Statistics, Mathematics Minor; GPA: 3.93/4.00\hfill January 2023 -- May 2025\\[-1pt]
\textbf{University of Michigan--Shanghai Jiao Tong University Joint Institute}\hfill Shanghai, China\\
Coursework toward a B.E. in Mechanical Engineering; First Class Scholarship\hfill September 2019 -- December 2020\\
transferred to UIUC
```

**Solution**: Moved "transferred to UIUC" to a separate line, allowing the date to stay properly aligned.

---

## Additional Technical Fixes

### 1. Table Formatting Issues (TCC & PostGrad Resumes)
- **Problem**: Skills sections used rigid `{ l l }` table format that didn't wrap text properly
- **Solution**: Added `\usepackage{array}` and converted to flexible paragraph columns with `>{\raggedright\arraybackslash}p{0.73\textwidth}`

### 2. Overfull Hbox Warnings
- **Problem**: Technical Skills tables exceeded page width, causing overflow
- **Solution**: Adjusted column widths:
  - EN2: `0.80\textwidth` → `0.74\textwidth`
  - KC: `0.80\textwidth` → `0.72\textwidth`
  - TCC: Added `\usepackage{array}` and reformatted table
  - PostGrad: Added `\usepackage{array}` and reformatted table

---

## Summary of Changes

| Resume | Issue Type | Fix Applied | Status |
|--------|-----------|-------------|--------|
| EN2 | Text overflow + Overfull hbox | Restructured education entry + column width | ✅ FIXED |
| ES | Text overflow | Restructured education entry | ✅ FIXED |
| KC | Overfull hbox | Column width adjustment | ✅ FIXED |
| TCC | Missing package + Overfull | Added array package + table restructure | ✅ FIXED |
| PostGrad | Missing package + Overfull | Added array package + table restructure | ✅ FIXED |
| CTA | None | No changes needed | ✅ OK |
| Appleton Lib | None | No changes needed | ✅ OK |
| Daniela | None | No changes needed | ✅ OK |

---

## Verification
All resumes now compile with zero LaTeX warnings:
- ✅ No overfull hbox warnings
- ✅ No underfull hbox warnings
- ✅ All text properly formatted and visible
- ✅ All dates properly aligned
- ✅ Professional appearance maintained

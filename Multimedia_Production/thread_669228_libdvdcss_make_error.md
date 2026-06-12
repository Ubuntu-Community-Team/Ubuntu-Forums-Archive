---
title: "libdvdcss make error"
date: 2008-01-16
forum: Multimedia Production
---

### Post by tuesday20102001 on 2008-01-16
I wanted to make a note for other users beating their heads against the desk over this error. ](*,)
Error: "! Package inputenc Error: Unicode char \u8:&#65533;ph not set up for use with LaTeX."
I came across several errors when using make
libdvdcss-1.2.9 from source. Error message towards make error.

exact error:
Writing index file refman.idx
No file refman.aux.
(/usr/share/texmf-texlive/tex/latex/base/ts1cmr.fd) [1] [2]
No file refman.toc.
[1] [2]
Chapter 1.
(./index.tex

LaTeX Warning: Reference `dvdcss_8h' on page 1 undefined on input line 5.

(/usr/share/texmf-texlive/tex/latex/base/t1cmtt.fd) [1]) [2]
Chapter 2.
(./files.tex

LaTeX Warning: Reference `dvdcss_8h' on page 3 undefined on input line 3.

) [3] [4]
Chapter 3.
(./dvdcss_8h.tex [5]

! Package inputenc Error: Unicode char \u8:&#65533;ph not set up for use with LaTeX.

See the inputenc package documentation for explanation.
Type  H <return>  for immediate help.
 ...

l.49 \item[Author:]St&#65533;ph
                        ane Borel $<${\tt [email]stef@via.ecp.fr[/email]}$>$
?

Then make hangs here until interrupted manually.

#solution!
#dependencies: bison doxygen linuxdoc-tools-latex g77 and other dependencies called for by .configure

#program fix is actually easier than previous forums suggest. upon meeting all dependency requirements: run ./confugure, then make (after configure completes, may need to run as sudo). you will receive a latex error with the following error St&#65533;ph. the question mark is acutally the problem (latex does not understand it because there is no translation for the french short e in Stephane Borel, thus the ?). type e and press enter, then wq! to save the file. rerun the make command again to recompile the code again. this should correct the error. lastly make install to finish the source compile.


should see something similar in running make script after recompiling:
(/usr/share/texmf-texlive/fonts/source/jknappen/ec/exillett.mf
 Ok [97] [98] [99] [100] [101] [102] [103] [104] [105] [106] [107] [108]
[109] [110] [111] [112] [113] [114] [115] [116] [117] [118] [119] [120]
[121] [122]) (/usr/share/texmf-texlive/fonts/source/jknappen/ec/exidigit.mf
 Ok [48] [49] [50] [51] [52] [53] [54] [55] [56] [57])
(/usr/share/ .

Hope this helps people.

---


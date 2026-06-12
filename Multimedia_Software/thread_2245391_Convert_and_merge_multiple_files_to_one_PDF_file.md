---
title: "Convert and merge multiple files to one PDF file"
date: 2014-09-23
forum: Multimedia Software
---

### Post by capslock4 on 2014-09-23
I am finding an application like Foxit Phantom in Windows operating system. 
Foxit Phantom is very useful for people who usually works with a lot of documents or books everyday. It can convert and merge a lot of files and also support for different file types such as docx, pptx, JPG,etc to unique PDF file with convenient bookmarks. Another great feature is that it is integrated into right click to use easily.
I have searched some applications but none of them has all the features like that. Could you recommend me any application as I described above?
Thanks in advance

---

### Post by tgalati4 on 2014-09-23
Open a terminal:

```
apropos pdf
```

It might look something like:

> tgalati4@Mint14-Extensa ~ $ apropos pdf
dvipdf (1)           - Convert TeX DVI file to PDF using ghostscript and dvips
evince-thumbnailer (1) - create png thumbnails from PostScript and PDF documents
fix-qdf (1)          - repair PDF files in QDF form after editing
foomatic-ppdfile (1) - Generate a PPD file for a given printer/driver combo
ghostscript (1)      - Ghostscript (PostScript and PDF language interpreter and previewer)
gs (1)               - Ghostscript (PostScript and PDF language interpreter and previewer)
gsnd (1)             - Run ghostscript (PostScript and PDF engine) without display
page-crunch (1)      - frontend to psutil programs, useful to manipulate Postscript and PDF files.
pdf2dsc (1)          - generate a PostScript page list of a PDF document
pdf2ps (1)           - Ghostscript PDF to PostScript translator
pdfdetach (1)        - Portable Document Format (PDF) document embedded file extractor (version 3.03)
pdffonts (1)         - Portable Document Format (PDF) font analyzer (version 3.03)
pdfimages (1)        - Portable Document Format (PDF) image extractor (version 3.03)
pdfinfo (1)          - Portable Document Format (PDF) document information extractor (version 3.03)
pdfopt (1)           - Ghostscript PDF Optimizer
pdfroff (1)          - create PDF documents using groff
pdfseparate (1)      - Portable Document Format (PDF) page extractor
pdftocairo (1)       - Portable Document Format (PDF) to PNG/JPEG/PDF/PS/EPS/SVG using cairo
pdftohtml (1)        - program to convert PDF files into HTML, XML and PNG images
pdftoppm (1)         - Portable Document Format (PDF) to Portable Pixmap (PPM) converter (version 3.03)
pdftops (1)          - Portable Document Format (PDF) to PostScript converter (version 3.03)
pdftotext (1)        - Portable Document Format (PDF) to text converter (version 3.03)
**pdfunite (1)         - Portable Document Format (PDF) page merger**
ps2ascii (1)         - Ghostscript translator from PostScript or PDF to ASCII
ps2pdf (1)           - Convert PostScript to PDF using ghostscript
ps2pdf12 (1)         - Convert PostScript to PDF 1.2 (Acrobat 3-and-later compatible) using ghostscript
ps2pdf13 (1)         - Convert PostScript to PDF 1.3 (Acrobat 4-and-later compatible) using ghostscript
ps2pdf14 (1)         - Convert PostScript to PDF 1.4 (Acrobat 5-and-later compatible) using ghostscript
ps2pdfwr (1)         - Convert PostScript to PDF without specifying CompatibilityLevel, using ghostscript
qpdf (1)             - PDF transformation software
roff2pdf (1)         - transform roff code into pdf mode



I don't know of a direct Foxit replacement.  Linux has a lot of low-level utilities for working with PDF files.  One would normally write a script using these utilities for performing repetitive actions using PDF's.  Understand that workflows in Windows do not translate to workflows in Linux.

With a little more searching, I found *pdfshuffler*:  [http://askubuntu.com/questions/2799/how-to-merge-several-pdf-files](http://askubuntu.com/questions/2799/how-to-merge-several-pdf-files)

---


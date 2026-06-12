---
title: "(Solved) Help manipulating 100page PDF file (slight rotation)"
date: 2013-10-01
forum: Multimedia Software
---

### Post by vap1485 on 2013-10-01
Greetings all. I'm a book publisher and I just got an order for a book that does not have a digital copy. I figured that I could scan the pages, and use that as the digital copy. Everything is working but I just noticed that the pages are slightly tilted. I suspect that it's because my scanner tilted each page as they were pulled in. So I wonder if there is a way to convert every page to an image file and batch rotate them to my liking. 

I would also like to know if there is a way to just rotate the whole PDF file in one action. 
Okay. Thanks

---

### Post by tgalati4 on 2013-10-01
tgalati4@Mint14-Extensa ~ $ apt-cache search pdf rotate
imagemagick - image manipulation programs
python-imaging - Python Imaging Library
texlive-latex-extra - TeX Live: LaTeX supplementary packages
texlive-latex-recommended - TeX Live: LaTeX recommended packages
latexdraw - vector drawing program for LaTeX using PSTricks
libpdf-reuse-barcode-perl - Create barcodes for PDF documents with PDF::Reuse
page-crunch - PDF and PS manipulation for printing needs
pdfmod - simple tool for modifying PDF documents
pdfmod-dbg - simple tool for modifying PDF documents -- debugging symbols
pdfshuffler - merge, split and re-arrange pages from PDF documents

I'm not familiar with these tools, so you will have to play with them.

If all of the pages have the same degree of tilt, then you might be able to use* imagemagick* in a script to rotate them and save them back out.

I just looked at *page-crunch*.  It only does + or - 90 degree rotation.

For rotating TIFF files (individual scans):

[http://linux.die.net/man/1/tiffcrop](http://linux.die.net/man/1/tiffcrop)

[http://www.linuxquestions.org/questions/linux-desktop-74/image-viewer-that-can-rotate-and-save-tiff-485772/](http://www.linuxquestions.org/questions/linux-desktop-74/image-viewer-that-can-rotate-and-save-tiff-485772/)

---

### Post by vap1485 on 2013-10-02
This helped me out somewhat. I found that I need to rotate it 1.4 degrees. No programs so far can rotate in anything buy multiples of 90 :/ 

PDFTK using mogrify

mogrify -rotate 1.40 MOTWM.pdf

this does the trick, but it kind of ruins the text

---

### Post by coldraven on 2013-10-03
Presuming that you have a folder with all the original scans as jpg or png
Using Gimp 2.8.2 you select File>Open as layers , select all the images with Ctrl+A
You can measure the angle with the measure tool, the angle is displayed at the bottom of the image.
Then you need to Link all the layers, there may be a way to "select all" but I don't know it.
[http://graphicssoft.about.com/od/gimptutorials/a/link-layers.htm](http://graphicssoft.about.com/od/gimptutorials/a/link-layers.htm)

Then select Layer>Transform>Arbitrary and enter the angle that you measured.
I just tried this with a bunch of my images so I did not want to save and ruin them.

---

### Post by tgalati4 on 2013-10-03
There is publishing and then there is publishing.  I've seen printed, paper books, you know the old-fashioned kind, that have been printed at a tilt or cut at a tilt.  You might need to rescan the pages with a way to fix or clean the page-feed wheels so that they get pulled in straight.  It's also possible that your scanner has some correction or calibration settings that you could use.  It's always better to fix the problem at the source.  If it was a scanning service, then you are out of luck.

If this is the very last copy of a paper book, consider having Google scan it and sell it through the Google Play store.

---

### Post by vap1485 on 2013-10-06
Thanks for the suggestion. I need physical copies though. 

coldraven:
I will try that. Thanks.

---

### Post by vap1485 on 2013-10-06
That was great. I opened the PDF in Gimp as a layer and it made every PDF page into a layer. I rotated them all, now how can I save it and it still be a book? Or do I have to save every layer individually?

EDIT: Yeah, trying to save them keeps asking me to flatten layers.

EDIT 2: That worked when I added a script called "Export Layers" to Gimp. [http://registry.gimp.org/node/25394](http://registry.gimp.org/node/25394)  

Now I have a new issue. When I export as images, the area that was rotated does not have the white background. It's has no background. Should I make a new forum post for that?

---


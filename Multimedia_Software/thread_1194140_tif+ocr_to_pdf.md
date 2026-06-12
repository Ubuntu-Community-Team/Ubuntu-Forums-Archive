---
title: "tif+ocr to pdf"
date: 2009-06-22
forum: Multimedia Software
---

### Post by Kikin-sama on 2009-06-22
I'm at a loss here. I'm looking for a command line tool that will convert from a tif file into a pdf that contains the text and images from the tif file.

I know I have to basically extract the text from the tif using tesseract, that will create a .txt containing the text from the tif. The problem is, how do I then merge the text with the tif into a pdf?

Any help will be appreciated...

---

### Post by ajgreeny on 2009-06-22
```
convert file.tif file.pdf
``` will do it all in one go if you have *graphicsmagick-imagemagick* installed (I think it is, by default).

---

### Post by Kikin-sama on 2009-06-23
That didn't do it. It's just as if it changed the file extension, no difference.

---

### Post by mvip on 2009-06-29
> **Kikin-sama said:**
> That didn't do it. It's just as if it changed the file extension, no difference.

Kikin-sama,

I'm looking to do the same thing. I posted a thread [here]("http://ubuntuforums.org/showthread.php?t=1198348&highlight=ocr"), but didn't find any solution either. I've managed to figure out the workflow fairly well up to the point where I need to merge the text document into the PDF file. Here's the workflow I have in mind (my work flow probably differs from yours):

 * ImageMagick to convert from PNG to TIF
 * Tesseract to perform OCR on the TIF file and output a plain text file with it
 * Missing step: Convert PNG/TIF to PDF with the text-file as a layer. 
  * I know PDF does support having a background layer of text behind an 'image layer,' I just haven't find a console tool that can do this. I've been looking at [PDFtk]("http://www.accesspdf.com/pdftk/"), which might be to do this. Unfortunately I haven't had the time to investigate it further.

I just thought I'd share my line of thought as it might help you too.

---

### Post by Kikin-sama on 2009-07-15
Couldn't find anything that would make the trick on the PDFtk docs. Interesting tool though...

I've come across a tool from [Vividata]("http://www.vividata.com/be_xtr_overview.html"), sadly you have to buy it after a 30 day trial period.

Does anyone knows of some free tool for the requested feature???

---


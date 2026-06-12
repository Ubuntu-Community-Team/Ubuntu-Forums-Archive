---
title: "Compress/Optimize a PDF document"
date: 2008-01-29
forum: Multimedia Production
---

### Post by MountainX on 2008-01-29
I have a 600MB PDF document that I need to get down to about 10MB. The last time I did this I used Adobe Acrobat Pro 8.0 on Windows. It has some automatic optimization functionality that will reduce the size of a PDF. How can I accomplish the same thing on Ubuntu? 

P.S. Should I post this in another section of the forum? 

Thanks.

---

### Post by MountainX on 2008-02-03
bump

---

### Post by Stochastic on 2008-02-04
If I was to take a guess at this (because I know very little about the pdf format or compression methods), I would say that you'll have to buy something from adobe to get that good of compression on a pdf file.  I guess this because pdf is not an open format but is owned by adobe.

---

### Post by orange2k on 2008-02-04
If this file contains pictures, then there is probably little you can do.
But if its only text, you could export it to a text file - sure it would lose much of the formating, but the information would be kept.

In Windows I know of a very good program that can do this: Abbyy PDF Transformer...

---

### Post by qazwsx on 2008-02-07
pdftk
[http://www.pdfhacks.com/pdftk/](http://www.pdfhacks.com/pdftk/)

KPDF (kprinter dialog) allows you reprint files as pdf (change image resolution etc). Some people tends to paste horribly big resolution images into their documents.:(

---

### Post by MountainX on 2008-02-07
Wow! This sounds like an incredible tool. You should post the link over here:
[http://ubuntuforums.org/showthread.php?t=382137](http://ubuntuforums.org/showthread.php?t=382137)

---------------------
[http://www.pdfhacks.com/pdftk/](http://www.pdfhacks.com/pdftk/)
If PDF is electronic paper, then pdftk is an electronic staple-remover, hole-punch, binder, secret-decoder-ring, and X-Ray-glasses. Pdftk is a simple tool for doing everyday things with PDF documents. Keep one in the top drawer of your desktop and use it to:

Merge PDF Documents

Split PDF Pages into a New Document

Rotate PDF Pages or Documents

Decrypt Input as Necessary (Password Required)

Encrypt Output as Desired

Fill PDF Forms with FDF Data or XFDF Data and/or Flatten Forms

Apply a Background Watermark or a Foreground Stamp

Report on PDF Metrics such as Metadata, Bookmarks, and Page Labels

Update PDF Metadata

Attach Files to PDF Pages or the PDF Document

Unpack PDF Attachments

Burst a PDF Document into Single Pages

Uncompress and Re-Compress Page Streams

Repair Corrupted PDF (Where Possible)

Pdftk allows you to manipulate PDF easily and freely. It does not require Acrobat, and it runs on Windows, Linux, Mac OS X, FreeBSD and Solaris.

---


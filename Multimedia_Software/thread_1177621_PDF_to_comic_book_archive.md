---
title: "PDF to comic book archive"
date: 2009-06-03
forum: Multimedia Software
---

### Post by houseonfire on 2009-06-03
I have PSPComic and I need to convert the 150 PDF files to comic book archives.
(.cbz, .cbr, .zip, .rar)
From what I gather, the Image files have to be in 01, 02 order. I think. I'm not sure.

Does anyone know of an application that can do this? I sure can't find one that is linux oriented.

---

### Post by minisori on 2009-06-03
The names of the files does not matter, the only need is that they are listed in the order you want them to show.

You can convert a pdf to images using an utility in xpdf package, after you compress all them in a rar file or a zip file and rename it to cbr or cbz.

sudo apt-get xpdf xpdf-utils

The program is called pdftoimages

---

### Post by houseonfire on 2009-06-04
The program I have views the image files from the archive.
I just need an app that can convert the pdf to images, and archive the images..
I had one for windows a long time ago, but I can't seem to find it now.

---

### Post by stinger30au on 2009-06-11
tried convert???

convert myfiles.pdf myfiles.jpg


hope this helps

---


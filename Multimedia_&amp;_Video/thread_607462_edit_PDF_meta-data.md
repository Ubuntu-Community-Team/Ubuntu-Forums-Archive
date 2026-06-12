---
title: "edit PDF meta-data"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by opakedragon on 2007-11-08
I want to edit the meta-data of a horribly screwed up PDF file I have. I like simple and this thing has so many objects to make a page that has text on top of a picture that is pretty much just a background anyway. Does anyone know of what can help? I've search with google these boards and most of what I find have those disgusting prerequisites: money and windows.

Thanks for your help.

---

### Post by MrFSL on 2007-11-09
[http://sourceforge.net/projects/pdfedit](http://sourceforge.net/projects/pdfedit)

---

### Post by Lemon on 2008-01-13
pdfedit doesn't edit meta data

I'm looking for a solution too!

---

### Post by ze_otter on 2008-01-13
I use BeCyPDFMetaEdit to edit the metadata in my pdf files. It's a Windows application, but runs fine with Wine. But I'd too like to know if there was an easy-to-use native Linux application for doing the same thing.

---

### Post by hoa3r on 2008-02-05
This tool can do it too and more: [http://www.pdfhacks.com/pdftk](http://www.pdfhacks.com/pdftk) 
Here is a tutorial but in german: [http://www.lagotzki.de/pdftk/index.html#metadata](http://www.lagotzki.de/pdftk/index.html#metadata)

@ze_otter thanks for the tip with BeCyPDFMetaEdit. With wine it's really easy to use. I noticed that drag and drop the PDF file in the window is possible too. Very nice :)

---

### Post by timothy.malone on 2008-02-27
There is a perl/tk script that uses pdftk to edit the metadata. You can get that here: [http://www.accesspdf.com/index.php?topic=toolslibs](http://www.accesspdf.com/index.php?topic=toolslibs)
You of course need perl, perl/tk, and pdftk. make the script executable and then run it. You can drag and drop a file, or you can you run it with a command line argument. I copied it to my /usr/local/bin directory and then right clicked on a pdf file, chose run with another application, then typed in the name of the script. The script is a little slow but it seems to work. Now tracker can find my pdf files.

---


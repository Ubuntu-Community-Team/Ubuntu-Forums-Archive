---
title: "How to convert a TIFF format into PDF format."
date: 2009-07-10
forum: Multimedia Software
---

### Post by bertilef10 on 2009-07-10
Hello guys, I need to convert a TIFF format into PDF. How can I do it?

---

### Post by bertilef10 on 2009-07-10
Hello guys, I need to convert a GIF image format into PDF. Pls help me.

---

### Post by bertilef10 on 2009-07-10
Hello guys, I need to convert a power point presentation into PDF. Pls tell me how to go about it.

---

### Post by s3a on 2009-07-10
Either gimp or imagemagick.

_With imagemagick:_

put the .tiff file into a folder called temp on your desktop then do:

sudo -i
apt-get install imagemagick; convert -units PixelsPerInch -density 150x150 *.tiff temp.pdf

Does that work for you?

---

### Post by bertilef10 on 2009-07-10
[COLOR=#993300][FONT=&quot]Hi guys, I need to create PDF documents from my MS Excel files. How do I do it?[/FONT][/COLOR]

---

### Post by bertilef10 on 2009-07-10
[COLOR=#993300][FONT=&quot]Hi guys, I need to create PDF documents from my word files. How do I do it?[/FONT][/COLOR]

---

### Post by ad_267 on 2009-07-10
Are you using OpenOffice in Ubuntu?

Just go to File - Export to PDF.

---

### Post by wojox on 2009-07-10
Hey try this:

1) Opened your excel file and click on File
2) Click Print, then changed the name of my printer to Adobe PDF then click on Properties.
3) Change the Default Settings under 'Adobe PDF Conversion Settings' to *Smallest File Size*.

That should do it.

---

### Post by wojox on 2009-07-10
Same as Excel

[http://ubuntuforums.org/showthread.php?p=7591958&posted=1#post7591958](http://ubuntuforums.org/showthread.php?p=7591958&posted=1#post7591958)

---

### Post by g00f on 2009-07-10
Open the file with Open Office ([www.openoffice.org]("http://www.openoffice.org")) and click the PDF button.

Works much better than the 'print to pdf' solutions as links, etc are preserved.

(Also works for Excel, Powerpoint and most other MS Office files that you've asked about minutes ago.)

---

### Post by ad_267 on 2009-07-10
Guys it's spam.

---

### Post by wojox on 2009-07-10
How do you know that? Just curious.

---

### Post by ad_267 on 2009-07-10
Click on their username and view all their posts under their profile. Then do the same for robinslo10.

robinslo10 is replying to all of bertilef10's posts with the magic-PDF link.

---

### Post by libra1780 on 2009-07-10
spam

---

### Post by gradinaruvasile on 2009-07-10
Open it in Openoffice Draw and click the PDF export icon...

---

### Post by kaibob on 2009-07-10
> **bertilef10 said:**
> Hello guys, I need to convert a GIF image format into PDF. Pls help me.
There are a lot of programs that will do what you want. One option is the convert utility, which is a part of the Imagemagick suite. 

```
convert input.gif output.pdf
```

I don't believe Imagemagick is installed by default. It's in the repositories and can be installed with Synaptic.

---

### Post by frodon on 2009-07-10
All similar threads merged.

Please one thread per request only.

---


---
title: "Converting and saving a PDF into JPEG"
date: 2012-04-25
forum: Multimedia Software
---

### Post by razedafear on 2012-04-25
Hi 

can somebody help me converting a pdf file to jpeg. I am using ubuntu 10.04. Is there a GUI alternative/software to do this. I have tried this method from command line but does not work :(

```
 convert -quality 100 -density 600x600 multipage.pdf single%d.jpg 
``` from here 
[HTML]  http://ubuntuforums.org/showpost.php?p=5560488&postcount=20[/HTML]

Thanks

---

### Post by texpat on 2012-04-25
Well, I just did a quick test and converted a pdf into a jpg like thus:
```
convert filename.pdf filename.jpg
```
and this worked just fine. Try omitting any extra arguments to start with and then play around with '-quality' '-density' and so on to see what happens.

If you want a GUI, you could use Gimp.

Good luck.

---

### Post by razedafear on 2012-04-25
> **texpat said:**
> Well, I just did a quick test and converted a pdf into a jpg like thus:
```
convert filename.pdf filename.jpg
```
and this worked just fine. Try omitting any extra arguments to start with and then play around with '-quality' '-density' and so on to see what happens.

If you want a GUI, you could use Gimp.

Good luck.

Got this error:- 

mark@mark-linux:~/Downloads$ convert adhaar.pdf adr.jpg
convert: unable to open image `adhaar.pdf': No such file or directory @ blob.c/OpenBlob/2480.
convert: missing an image filename `adhaar.jpg' @ convert.c/ConvertImageCommand/2838.

---

### Post by Zimmer on 2012-04-25
Quick answer, open the pdf in GIMP and deal with the loaded layers as you wish,  and save as... jpg, or any other GIMP supported export format.
EDIT:
from your error message, it could be as simple as you not being in the correct directory that the pdf file is stored in....

---

### Post by forrestcupp on 2012-04-25
> **texpat said:**
> 
If you want a GUI, you could use Gimp.

Good luck.

Cool. I didn't know that Gimp can import pdf files.

---

### Post by razedafear on 2012-04-25
> **Zimmer said:**
> Quick answer, open the pdf in GIMP and deal with the loaded layers as you wish,  and save as... jpg, or any other GIMP supported export format.
EDIT:
from your error message, it could be as simple as you not being in the correct directory that the pdf file is stored in....

Kool, gimp works for me.! btw: the file was in Home/Downloads :)

---


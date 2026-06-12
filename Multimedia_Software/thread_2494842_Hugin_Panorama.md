---
title: "Hugin Panorama"
date: 2024-01-28
forum: Multimedia Software
---

### Post by ubontik22 on 2024-01-28
Hello,

I've created a panorama **.pto** file. How to convert one to **.jpg** or **.png**?

Thank you.

---

### Post by #&amp;thj^% on 2024-01-28
EDIT: Please make a back-up or copy of the image/s your going to convert for safety
Using ImageMagick.

```
sudo apt-get install imagemagick
```
Just for good messure
Try converting just one image at first:
```
convert image.jpg image.png
``` 
 use the mogrify command. This is an excellent tool from ImageMagick for all our image manipulation needs.
```
mogrify [options] input-file
```

Lets say we have this:"Tracks1.png  Tracks2.png"
we use:
```
 mogrify -format jpg *.png
```
While the mogrify command edits the files in place, the convert command puts the result in a new file.

Usage is:
```
 convert *.png Tracks.jpg
```

Clear as mud right?

---

### Post by ubontik22 on 2024-01-28
Thank you,

But I want to convert [COLOR=#000000]Hugin Panorama file (.pto) to .jpg or .png format and be able to open.[/COLOR]

---

### Post by #&amp;thj^% on 2024-01-28
Sorry thought pto was a type o for photo
Please see this: [https://hugin.sourceforge.io/docs/manual/Panorama_scripting_in_a_nutshell.html](https://hugin.sourceforge.io/docs/manual/Panorama_scripting_in_a_nutshell.html)
Start here>>>Example work flow similar to assistant in Hugin GUI

---

### Post by ubontik22 on 2024-01-29
I noticed when I ran Batch several files were missing. I deleted them from the batch list ran again, and it worked.

---

### Post by TheFu on 2024-01-30
> **ubontik22 said:**
> Thank you,

But I want to convert [COLOR=#000000]Hugin Panorama file (.pto) to .jpg or .png format and be able to open.[/COLOR]

The pto file isn't an image. It just provides the list of other image files to be included in the completed pano image.   It is hugin specific.

My camera prefaces pano images with STA- .... STZ- to keep them in order.

---


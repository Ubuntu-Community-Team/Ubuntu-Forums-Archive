---
title: "Actions in Gimp"
date: 2008-03-28
forum: Multimedia Production
---

### Post by rolodoom on 2008-03-28
I need to convert a lot of jpg, png images to Tiff, Grayscale 300 dpi. Is there any way to record the action for one image and repeat it for the rest?

Thanks,

---

### Post by kayosiii on 2008-03-28
currently the only way to do this is to write a script for gimp. You can do this in a number of scripting languages I know that guile (lisp), Python and Perl are supported. Currently there isn't the equivelent of a macro recorder in the gimp.

If you are just resizing you might concider a program like digikam which is designed to work with lots of images. It has quite a few batch processes already built in.

---

### Post by cotcot on 2008-03-28
Image Magick is able to do that with the mogrify command from the directory with you images :
```
mogrify -format tiff *.jpg
```

---

### Post by rolodoom on 2008-04-29
Is there a chance to also convert to 300dpi using mogrify??

---


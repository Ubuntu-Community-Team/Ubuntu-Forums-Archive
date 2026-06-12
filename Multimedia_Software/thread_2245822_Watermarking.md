---
title: "Watermarking"
date: 2014-09-26
forum: Multimedia Software
---

### Post by Ifaistos on 2014-09-26
Hello everyone :-)

I am looking for the easiest, fastest way to watermark my pictures.
It seems that aphoto doesn't work, and that there is no other easily installable program (with GUI) that can do the trick.
Any suggestions please?

Thank you all

---

### Post by Vladlenin5000 on 2014-09-28
Here's one: [http://www.daanav.com/watermark-software-for-linux/](http://www.daanav.com/watermark-software-for-linux/)

---

### Post by Ifaistos on 2014-09-28
This is an excellent tool !!

Thank you so much :-)

Do you know if there is a way to Resize without the percent?
I was wondering if there was a way to resize to certain width or certain height.  eg.  Resize all images to 613 pixels wide.

I know I can do that with Gimp, and frankly I will do that.... 
But it would help a lot if I could do that with this software...

Thank you again !!

---

### Post by Vladlenin5000 on 2014-09-28
You're welcome.

The truth is I just came across that piece of software by googling after your request. I never used it before.

---

### Post by Ifaistos on 2014-09-28
Thank you for your time!!

It is an excellent tool, but it can't do what I want...
I am using Gimp with scripts now...

Problem is that I have to do each photo individually.
It would be great if I could find a software to resize to certain pixel width, and add a picture and text watermark.

Right now I am using two scripts I found here

[http://www.skipser.com/p/2/p/how-to-watermark-photos-using-gimp.html](http://www.skipser.com/p/2/p/how-to-watermark-photos-using-gimp.html)

They do the job, but not resizing, and not collective watermarking...

btw.. Does anyone know if there is a way to resize a group of images using gimp to a certain pixel width?

Thanks again.

---

### Post by Pinoy Tux on 2014-09-28
Try Phatch (PHoto bATCH processor).

---

### Post by varunendra on 2014-09-29
A BIG +1 to Phatch. I used it personally sometimes ago (although now I prefer the command line tools like "convert" and "mogrify" of Imagemagick package), and it worked wonderfully.

Another good thing about it is that it seems to always preserve the source files and save the processed files as new copies in a different directory. But it is always recommended to backup your source files yourself first, not rely on any software for that.

Watermarking (quite flexible) is just one of the hundred other tasks it can perform on images in batch mode (multiple images at once).

Keep in mind that it is not an image editor itself, it is just a GUI tool to perform chosen actions on a list of images in batch mode, and often uses other programs in the background, itself serving only as a front-end to select the actions. Most of the actions are flexible/adjustable, but some may not be.

---


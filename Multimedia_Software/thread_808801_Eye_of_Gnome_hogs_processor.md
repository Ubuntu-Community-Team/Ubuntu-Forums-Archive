---
title: "Eye of Gnome hogs processor"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Endolith on 2008-05-26
Whenever I use the default viewer (Eye of Gnome 2.22.1) on digital camera images, the CPU maxes out for periods of about 8 seconds and I can't do anything.  Does anyone else see this problem?  If I go to the next image, for instance, the next image displays fine.  If I then press the zoom in command, the image zooms in instantly, but then the processor suddenly maxes out and stays that way for 8 seconds.  It's already displayed the zoomed-in image, so it's not processing that.  It doesn't seem to be doing anything, except using the processor.  Opening Eye of Gnome maxes out the processor.  Closing it maxes out the processor.  The System Load ramps up.  I don't know what it's doing.

---

### Post by Jon Monreal on 2008-05-26
I used to use Eye of Gnome, but was unsatisfied with it and experienced some similar problems on a smaller scale.

I have switched to gThumb since and have been much happier with it. You might decide to try it, you could simply install it using Add/Remove Applications.

Otherwise, you might try using another image viewer of your choice.

At any rate, feel free to post what happens and to PM me. Hope this works for you.

---

### Post by Endolith on 2008-05-26
> **Jon Monreal said:**
> I have switched to gThumb since and have been much happier with it. You might decide to try it, you could simply install it using Add/Remove Applications.

gThumb does appear to be about a billion times faster.  I guess I'll have to learn to use it for everything.  Is Eye of Gnome used by Nautilus, though?  I seem to get the same kinds of slow downs with thumbnails.

---

### Post by mtopro on 2009-01-17
I can also confirm the Eye of Gnome is a processor HOG.  Also confirm the thumbnail issue hogging the CPU.  It helps to delete all files under '.thumbnails' in the home/user folder.
Installed gthumbs for a much better experience, however it does seem that Nautilus is tied to this issue and is only corrected by the clearing of thumbnails as mentioned above.

---

### Post by Endolith on 2009-01-18
There was supposed to be a limit on the amount of disk space that could be used up by thumbnails, but it doesn't appear to have been implemented.  :/

---


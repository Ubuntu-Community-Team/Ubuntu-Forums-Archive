---
title: "Which webcams works with Ubuntu Fiesty?"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by xarroyo on 2007-06-18
Hi,

I am new using Ubuntu. I was searching in google but i haven't found which webcams works with Ubuntu... it would be nice if someone shows a list of the camaras that works with Ubuntu.. I have the Tripplite Clip Camara but it seems it doesn't work..

Please, i need help with this..

Thanks for you attention,

Xavier

---

### Post by dabl on 2007-06-18
Logitech QuickCam Communicate

:)

---

### Post by xarroyo on 2007-06-19
The logitech webcam is the only webcam that works with ubuntu?? how about the HP laptops that comes with an integrated webcam? 

Is it logitech the only option?

---

### Post by Bill Cosby on 2007-06-19
Basically every webcam which can run with the uvc driver is a good choice for Linux, have a look [here]("http://linux-uvc.berlios.de/#devices"), there is a list with webcams known to work
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by eggy1962 on 2007-06-19
i have two webcams available  one is ezonics which when plugged in works but pic is so dark is unusable and whatever is installed that runs it driver wise is poor as it does not respond to controls for brightness etc
number two is a phillips spc900nc which i know works when plugged into pclinos yet does not in ubuntu ff using same program....it lights up led wise but no pic on screen just black screen....so i am not sure why its not working properly in ff where its very good in pclinos
ps the program i was using...kopete....
ps  again just tried it in xawtv out of curiosity and its working there... so must be something to do with kopete and feisty

---

### Post by crispy_420 on 2007-06-19
The one in my Acer 5100 series worked right away.

---

### Post by gimmy_bond on 2007-06-19
I have just tried Logitech Cam Expresss (P/N 861-050-xxx), it seems to work. Tried it with XaTV, a bit hard  to use the adjustments. but I can't find a s/w driver for this webcam

---

### Post by eggman jr. on 2007-06-21
eggy1962:

I had the same problem with the Phillips SPC900NC as you. To get it working, I opened "Multimedia Systems Selector" in Preferences and changed the default video output plugin to "X Window System (No Xv)". It now works fine in Camorama and Ekiga.

If you can't find the Multimedia Systems Selector in Preferences, right-click the Applications menu, and choose Edit Menus. Check the box to make it appear in the menu

---

### Post by eggman jr. on 2007-06-21
> **eggman jr. said:**
> eggy1962:

I had the same problem with the Phillips SPC900NC as you. To get it working, I opened "Multimedia Systems Selector" in Preferences and changed the default video output plugin to "X Window System (No Xv)". It now works fine in Camorama and Ekiga.

If you can't find the Multimedia Systems Selector in Preferences, right-click the Applications menu, and choose Edit Menus. Check the box to make it appear in the menu

Of course, now I no longer have video playback, just a black square with sound. This is on Feisty, btw. Gutsy seems to work fine.

---


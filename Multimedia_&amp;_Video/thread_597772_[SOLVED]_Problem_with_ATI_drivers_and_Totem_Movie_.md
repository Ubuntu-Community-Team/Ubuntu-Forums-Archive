---
title: "[SOLVED] Problem with ATI drivers and Totem Movie Player"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by brunolabs on 2007-10-30
Hi all!

I installed Ubuntu Feisty in a PC with an ATI X700 SE graphic card and everything worked great except the low screen resolution.
After installing the ATI accelerated graphics driver from the &#8220;Restricted Driver Manager&#8221; the screen resolution and quality are excellent but the image quality in Totem Movie Player when playing video files gets much worse (pixelized) then it was when running without the graphic drivers (it was perfect btw)!
I also tried installing the drivers by using the official ATI package from their website but the problem remains. Also used the option &#8220;deinterlace&#8221; with no success.

Anyone can help?


Thanks

---

### Post by touchwood on 2007-10-30
I am running an X1700 on an Asus laptop - I have not managed to get 3D working but video playback seems ok.

---

### Post by brunolabs on 2008-01-14
Can anyone help me please?

It's really the only thing keeping me from completely changing to Ubuntu. :(

I've posted an attachment with a screenshot so you can see what's happening (notice the letters are pixelized).


Thanks.

---

### Post by eye208 on 2008-01-14
Enter the following command into a terminal window:

sudo aticonfig --ovt Xv

This will enable the XVideo extension in the proprietary ATI driver which is disabled by default. XVideo is required for non-pixelized video playback in Totem.

The new setting will be saved to the X.org config file.

---

### Post by brunolabs on 2008-01-14
Thanks! It works! :)

---


---
title: "Matrox G550, DVI and Dapper = Out of Range"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by macar on 2006-06-03
Hi!

I've just tried the (K)ubuntu Dapper Desktop CD and it's great, except one problem I'm experiencing: namely I use Matrox G550 video card connected over the DVI output to my LCD display and the problem is that.. it doesn't work :). I simply get "out of range" message on my screen while the system thinks it's OK and continues to load the desktop.

So far I've found two workarounds: one is to use "vesa" driver instead of the "mga", another is to connect via analog cable.

Has anyone experienced similar problems and can provide me with a simply but functional ;) solution?

Thanks in advance,
M.

---

### Post by Daliz on 2006-06-04
I have the same problem.. I'm not an expert, but as far as I know, it's because the driver needs the HAL (or whatever) library to make DVI functional. The driver, along with the needed library, can be downloaded from Matrox website. The real problem is, that the library isn't compatible with Xorg7.x. There is a workaround, although I haven't tried it yet, check the forums at Matrox.com.

---

### Post by Silen on 2006-06-04
To all of you with a Matrox, there's a script here, that automatically fixes the MGA driver:

[http://www.tuxx-home.at/archives/2006/06/04/T14_46_29/](http://www.tuxx-home.at/archives/2006/06/04/T14_46_29/)

---

### Post by Daliz on 2006-06-05
Yap, there is a script, but it doesn't work..
It says that i have to install "imake" even though it's installed! :D

---

### Post by rutx on 2007-10-21
It doesn't work for me either...:(

---

### Post by jp734 on 2008-06-08
I also have G550 using the unofficial 4.4.4 driver at [http://www.tuxx-home.at](http://www.tuxx-home.at) - I don't see an out of range message but every time I connect my tv on the dvi connection, it is only showing it on 640x480 and it is not centered.

you will find my xorg.conf file here:
[http://ubuntuforums.org/attachment.php?attachmentid=73418&d=1212972895](http://ubuntuforums.org/attachment.php?attachmentid=73418&d=1212972895)

---


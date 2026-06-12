---
title: "X11 failing w/new card - how to reprobe for video?"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by barrmulio on 2006-05-27
I swapped out from a integrated intel card to a old bfx geforce 5500 oc that i swapped out of another pc.  Now I'm getting a error "failed to start the x server"

the output has:
-*-*-*-*-*-*-*-*-*-*-*-*-*-*
(EE) failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) failed to load module "GLcore"(loader failed, 7)
(EE) No devices detected

failed server error: no screens found
-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*

when I look at the device in xorg.conf it's still stating "Intel Corporation 82865G Integrated Graphics Device" - I'm assuming that's the problem (note: it is diabled in bios now)

I can only get in through command line (unless I remove the geforce card) - how do I force a reprobe for hardware during boot or edit my x11 config for the right video card?  

Thanks in advance

edit: I popped in a live 5.04 cd i found around and it worked great...

---

### Post by barrmulio on 2006-05-27
i got a pm on the fix - thanks for the quick help

for those who need it:

- sudo nano /etc/X11/xorg.conf
- find the Device section, change the pci settings to 1:0:0 and driver to nvidia
- find the Screens section, change the device to the name you placed in the device line
- sudo reboot

if you don't want a nvidia logo add the line
Option "NoLogo" 
beneath the Device Section

---

### Post by index_0@ya.com on 2006-05-30
so how do i do it for other than nvidia/ati ? 

say , i've VIA/S3G internal graphics card, wht needs to be written?

---

### Post by az on 2006-05-30
This is a problem that needs to be addressed.  This should be done automagically.  You can get the xorg package to redetect the hardware, just like when you first installed.


You need to
1.  boot into recovery more

2.  run
dpkg-reconfigure -phigh xserver-xorg

3. run
init 2

It's as simple (but cryptic) as that.

---


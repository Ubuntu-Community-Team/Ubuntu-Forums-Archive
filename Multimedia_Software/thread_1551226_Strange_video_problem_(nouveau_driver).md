---
title: "Strange video problem (nouveau driver?)"
date: 2010-08-12
forum: Multimedia Software
---

### Post by website.reader3 on 2010-08-12
I have a problem that is occurring in both openSUSE 11.3 and Ubuntu 10.4 and concerns my GF8400GS video card which supports both VGA and DVI.  The problem, as I have been able to localize it, seems to be coming from an interaction with the vbe parameters set by grub and some timing issues and when the graphics card is probed to determine the proper setup mode by X windows.

After working with both OS's which ran grub to create a boot selection during boot up, the video card would only run in VGA mode only.  However, and this is a big key, running the Ubuntu 10.4 install CD seems to wake up the card into DVI mode correctly.

I did notice that someone said to set things to the GDM manager, and not use KDE, but I was using GDM to start.

I really want to get this card working in DVI mode, and went through a long struggle on the openSUSE forums trying to get it working, and finally gave up when other problems ensued.

I was elated, the first time I installed Ubuntu 10.4, because things seemed to work correctly.  Now I am stuck in VGA and cannot escape.  I even played with the vbe parameters in the /etc/default/grub file (and ran update-grub) but the changes have had no such luck in restoring DVI mode.

Nvidia claims that their drivers are guaranteed to work in linux, will I have to install their drivers instead of the nouveau module?  openSUSE has a huge web page on the problem of getting video cards to work in regard to the nouveau kernel module.

Any ideas?? It's already been 5 days and my colleague is asking me to produce work, not answer him with "I am still struggling with system problems"

Randall

running xrandr shows

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192                                 
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DVI-I-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080      60.0 +   50.0* 
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       50.0     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        60.0 

but the Samsung 2494 monitor insists that NO dvi signal is being received.

---

### Post by ghettobird on 2010-08-12
system>admin>hardware drivers>nvidia-current
I can't remember if the current driver works for the GPU's above the G92 which is on the 8800 GT. Nouveau has never worked for me probably because it's reverse engineered. If you have time and patience download the driver from Nvidia's site, shut down x-server and cd download to install the official driver.

---

### Post by website.reader3 on 2010-08-12
Okay, this is a wonderful improvement, I can see the Nvidia X server settings under the System -> Administration -> tab.

But I do not have the mouse in the DVI-I window.  How do I get the mouse to show up?

Randall

---

### Post by website.reader3 on 2010-08-12
Found out by experimenting that the VGA screen HAS to be disabled for the mouse and keyboard to correctly work in the DVI screen.

All is well now, but this has taken awhile to accomplish.

---


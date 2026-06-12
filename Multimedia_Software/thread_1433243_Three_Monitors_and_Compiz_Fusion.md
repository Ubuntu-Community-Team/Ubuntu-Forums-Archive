---
title: "Three Monitors and Compiz Fusion"
date: 2010-03-18
forum: Multimedia Software
---

### Post by tekgeek on 2010-03-18
Hello all,

I have have been using Ubuntu for a while, and have recently upgraded to three monitors, on 9.10.  However, in order for all 3 monitor to be able to be used correctly, I have had to enable Xinerama (I am running two 9600 GSO's), which seems to break compiz.  

However, I think this may be able to be fixed.  I found this post:  [http://ubuntuforums.org/showthread.php?t=884161]("http://ubuntuforums.org/showthread.php?t=884161")   , which describes how someone set up six monitors using Xgl.  I have installed Xgl, and have gotten the following:

$ compiz
**Checking for Xgl: not present.** 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
Xlib:  extension "RANDR" missing on display ":0.0".


Essentially, what i am asking is, is there any way to enable Xgl on ubuntu 9.10 so that I can use Compiz?

Any help is greatly appreciated.

Tekgeek

---


---
title: "MPEG2 Hardware acceleration Via Epia"
date: 2010-01-26
forum: Mythbuntu
---

### Post by alex341 on 2010-01-26
I'm building a HTPC, based on a Via Epia EX10000EG with a Haupauge PVR 500 dual TV tuner card. I started out with an installation of Mythbuntu 9.10. With a lot of trouble I created a new kernel to get rid of the spontanious reboots, struggled my way trough lots and lots of forum discussions about mythfilldatabase, finaly had my sound working, but now I'm faced with slow video when playing recorded programs.
 
Allthough I have all kind of modules loaded in xorg.conf (dri, glx, etc), I can't get my MPEG2 hardware decoding to work.
 
I've tried all kind of drivers, settings, patches, but I can't get it to work. Who knows how to activate / use the MPEG2 hardware decoder?

---

### Post by LowSky on 2010-01-26
Via has never played very well with Linux, sorry for the pain.

Maybe this will help
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by ian dobson on 2010-01-26
Hi,

Via has always been the odd man out. Have a look at [http://www.minimyth.org/](http://www.minimyth.org/) it's a special mythtv/via distribution.

Regards
Ian Dobson

---

### Post by alex341 on 2010-01-27
@ LowSky: tried all the Via drivers, but without the desired result. Various forums claim that the only way the Via Epia MPEG2 Hardware Acceleration will work is with the OpenChrome driver. I got that driver (available in the Mythbuntu 9.10 DVD), but can't get the hardware acceleration to work.
 
@Ian Dobson: I don't have a PC to spare, so I want to build a frontend/(master)backend system. Minimyth is a frontend or a frontend/slave backend system. And, although it is build for Via, the Via Epia EX isn't among the supported hardware...
 
The problem: I heard people with similar hardware who got it to work. The only problem is: they don't know how and he is (as well as I am) not a real Linux specialist.

---


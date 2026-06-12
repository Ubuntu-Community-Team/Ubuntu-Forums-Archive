---
title: "Resolution problems with some Nvidia cards"
date: 2008-05-17
forum: Multimedia Software
---

### Post by vitorgatti on 2008-05-17
Hi,

I don't know what's happening to this version of Ubuntu, but the Nvidia restricted drivers installed with Ubuntu or with EnvyNG are not working properly with, for example, 2 video-cards I've tested in 2 different PCs.

NOTE: both using a 15' CRT Monitor

1°) GeForce 4 MX400 64MB
Without any restricted drivers, I can only select 640x480 and 800x600 resolutions. After installing (with Ubuntu or EnvyNG), max resolution is 320x240. Hell yea, it's impossible to use this system with that... hehe

2°) GeForce 6150SE (OnBoard)
Without any restricted drivers, I can only select 640x480 and 800x600 resolutions. After installing (with Ubuntu or EnvyNG), max resolution is 640x480.
This, with EnvyNG, asked the resolutions that I wanted. After choosing 1024x768, Ubuntu starts, sound plays, but all in a black screen...

On both I tried to run "dpkg-reconfigure xserver-xorg", but there isn't anymore the part of choosing resolutions.
I've also tried to edit "/etc/X11/xorg.conf", but I didn't find the resolutions part.

NOTE:
3°) GeForce FX 5700 LE 256MB AGP 8x (in a 17' CRT Monitor)
All worked great with Ubuntu's restricted drivers (not using EnvyNG).

What's really happening? In Ubuntu 7.10 all worked nice...

Thanks

---

### Post by vitorgatti on 2008-05-18
No ideas of what's happening?

---

### Post by TatuSalin on 2008-05-18
> **vitorgatti said:**
> No ideas of what's happening?

Hello. I got same problem on my laptop. There is only 600x800 and 480x640 resolutions available on the Ubuntu. 

Luckily you should be able to use ctrl + (+-button) to resize screen. You should be able also to use maodify screen text and pictures size from the browser.

:guitar:

---

### Post by vitorgatti on 2008-05-18
Thanks for the tip, but this isn't the real solution for the problem...
And with resolution 320x240, it's impossible to use the system, as some windows won't, even very small, fit in the screen.

---


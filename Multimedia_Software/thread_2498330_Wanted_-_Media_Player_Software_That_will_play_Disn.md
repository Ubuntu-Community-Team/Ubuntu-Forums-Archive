---
title: "Wanted - Media Player Software That will play Disney DVDs"
date: 2024-06-09
forum: Multimedia Software
---

### Post by AlexHudghton on 2024-06-09
I normally use VLC as a media player, to play films on DVD or 'converted' from DVD. This has worked well for me for over 15 years

In the last year or so I have come across a problem in that DVDs from Disney will not play without constant freezing / stuttering / black screens

I have 8 films in this category (out of my library of 1000+).

I have tried using SMPlayer and that reduces the stuttering to an acceptable level, bit I'd rather have none.

SMPlayer won't work on the latest (to me) releases, in particular Lightyear and Zootropolis (UK title)

I don't want to copy / rip the disk, I just want it to play in the DVD drive.

Anyone know of any software to make this happen?

(Poking around in VLC cache and other settings does not change anything, I may be retired, but I have better things to do)

---

### Post by currentshaft on 2024-06-09
Have you tried them on other devices/operating systems? I mean, what makes you think it's an issue with software/Ubuntu? I would start to question DVD lifespan after a decade ...

---

### Post by Tadaen_Sylvermane on 2024-06-09
libdvd-pkg is the package you want. and after you install it you need to manually run ```
dpkg --reconfigure libdvd-pkg
``` Even after this the disc may not play perfectly but it should work for the most part. On Windows VLC comes with libdvdcss as part of the package. Linux you need it externally, most likely so that it doesn't contain non free software, in this case the libdvd-pkg package actually runs a script that downloads it from the vlc archives. It doesn't actually contain the needed file itself.

---

### Post by AlexHudghton on 2024-06-10
Thanks for the replies 

A little further explanation

I have a dual boot Ubuntu 22.04.4 / Windows 10 desktop and a Ubuntu 22.0.4.4 laptop

All the DVDs I have are ripped to disk, apart from the few that I have to run from the DVD disk itself.

The disks I am having problems with have all been purchased in the last year or 2 - Lightyear and Zootropolis in the last 3 months. (and they are all produced by Disney)

The problem disks exhibit the problem on both platforms with VLC / SMPlayer 

The only platform I don't have is a TV.

I have the latest version of libdvd-pkg installed

---


---
title: "ripping to MKV but loosing half the DVD"
date: 2012-09-22
forum: Multimedia Software
---

### Post by afulldeck on 2012-09-22
I ripping to mkv with handbrake, but I am missing the later chapters. I've included the extra libraries. Anyone have any clues as to why I would be missing the later chapters. Should I use another tool? I would like to break this up into small chapters.

I should add, that I'm ripping an iso file with  Braser and and I watch it with VLC. I was trying to use handbrake to break it up into chapters for a montage.

Correct me if I'm wrong, but I think this is the offending part.

libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/SWEEP for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/afulldeck/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8

Can't read name block? Unable to find map? I did load libdvdread4 and install css...what's happening does anyone know?

---

### Post by afulldeck on 2012-09-23
Bump. Anyone?

---

### Post by afulldeck on 2012-09-24
I've re-loaded libdvdread4 and installed css.sh....but no change. I seem to only get the first part of the dvd. Does anyone have any suggestions that I can try?

---

### Post by Steeperton on 2012-09-25
What DVD is it? I had trouble with some Disney ones ("Up" was the worst), because they’ve got a weird copy protection that gives 99 titles, all of the same (apparent) length but when ripping it's either out of sequence, or cuts off early.

Open the DVD in VLC (or similar) then note which title you're watching (i.e. find out the "true" title). Then manually select this title in handbrake.

---

### Post by afulldeck on 2012-09-25
Well, I think I might have found the problem. I was able to rip it with makeMKV.  Apparently,  this particular dvd has 34 chapters. The second 17 chapters where label exactly the same as the first 17 chapters. Handbrake stops at the end of the chapter 16 and doesn't rip the second 17 chapters. I now think handbrake finds the second chapter 1 and ejects....

---


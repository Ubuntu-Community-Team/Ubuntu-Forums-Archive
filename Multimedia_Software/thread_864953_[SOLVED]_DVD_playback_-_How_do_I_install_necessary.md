---
title: "[SOLVED] DVD playback - How do I install necessary packages"
date: 2008-07-20
forum: Multimedia Software
---

### Post by charonred on 2008-07-20
I´m trying to get DVD playback working and am trying to follow the instructions on this thread,
[URL="http://ubuntuforums.org/showthread.php?t=766683"]
http://ubuntuforums.org/showthread.php?t=766683[/URL]

but I don´t know how to fix these things, I´m just not familiar with the Terminal an dhow to do things with it.

I´ve tried this in Terminal and Update Manager, but keep getting this error

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

how do I fix ?

---

### Post by dexter.deepak on 2008-07-20
just follow what the error message says...open up a terminal and simply copy-paste this:
```
sudo dpkg --configure -a
```
report back if the problem persists.

---

### Post by charonred on 2008-10-01
If you use a 32-bit (or 64-bit for a lot fewer supported codecs) you can check this out:
[http://www.medibuntu.org]("http://www.medibuntu.org")
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

The packages you require are:
- w32codecs or w64codecs
- libdvdcss2
- libdvdread3
- mplayer

---


---
title: "VLC Media Player - Video Problems"
date: 2009-11-07
forum: Multimedia Software
---

### Post by JustinR on 2009-11-07
I've been using Xubuntu (Karmic Koala) on a Dell Inspiron 1720 with a nVidia graphics card driver I installed from the Hardware manager (NVIDIA accelerated graphics driver Version 185) and I get no video output from VLC, no matter what video output method I select in it's preferences, nothing works.

So I ran VLC in a terminal with my dvd inserted that I wanted to watch and it returned this:

EDIT: I've also experienced a lot of kernel panics/unresponsivness and have had to run fsck many times and it reports corrupted/damaged files/blocks a lot - maybe that has something to do with the problem.

"justin@xubuntu-fd:~$ vlc /media/cdrom0
VLC media player 1.0.2 Goldeneye
[0x8463518] main interface error: no interface module matched "globalhotkeys,none"
[0x8463518] main interface error: no suitable interface module
[0x83ba140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x83ba140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/justin/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f00000. Regions: 1 2 3 4
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0xb7400738] main input error: ES_OUT_RESET_PCR called
[0xb7400738] main input error: ES_OUT_RESET_PCR called
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0xb7400738] main input error: ES_OUT_RESET_PCR called
[0xb7400738] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
"

What can I do? I've read the forum - and followed the Comprehensive Multimedia and Video How to and that didn't work.

---

### Post by mc4man on 2009-11-07
try running this from a terminal and see if it installs libdvdcss2, if so, then try vlc again
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by JustinR on 2009-11-07
Thanks for your reply!

Wow! It works - that saved me a lot of time,

thank you!

---


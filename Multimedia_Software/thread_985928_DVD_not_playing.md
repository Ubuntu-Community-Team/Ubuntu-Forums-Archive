---
title: "DVD not playing"
date: 2008-11-18
forum: Multimedia Software
---

### Post by Bofur on 2008-11-18
Hi I'm having problems playing a dvd series I purchased. I have the restricted drivers installed and all(I think) codecs required for it to work. Heres what happens when I try opening it up:

```
justin@ubuntu:~$ vlc /media/cdrom0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/justin/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
justin@ubuntu:~$ 

```Any help would be much appreciated!

---

### Post by Bofur on 2008-11-18
Bump

---

### Post by Bofur on 2008-11-18
Bump!!

---

### Post by mc4man on 2008-11-18
>  Encrypted DVD support unavailable.

you need libdvdcss2


Go here and add medibuntu to your sources as described. (add repo line and then the add key line (from terminal
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) 

then add from synaptic or run in terminal
```
sudo apt-get install libdvdcss2
```

Or go here and download and install libdvdcss2 (probably the i386 package unless your running the 64 bit ubuntu then amd64 one

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)


Edit
It says intrepid but works on all recent ubuntu releases

---


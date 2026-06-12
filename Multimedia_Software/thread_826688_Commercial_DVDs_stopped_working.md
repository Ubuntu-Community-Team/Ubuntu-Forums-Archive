---
title: "Commercial DVDs stopped working"
date: 2008-06-12
forum: Multimedia Software
---

### Post by DrQuincy on 2008-06-12
I've been watching commercial DVDs on this machine for a year or so, no probs. Now commercial DVDs won't play. The drive is fine as non-encrypted DVDs, i.e. data DVDs are okay. A commercial DVD just freezes any player I use. If I run VLC in the shell and open a DVD I get this:

```
tim@kubuntu:~$ vlc
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: DVDVolume
libdvdnav: DVD Serial Number: cb0282c5        
libdvdnav: DVD Title (Alternative): DVDVolume
libdvdnav: Unable to find map file '/home/tim/.dvdnav/DVDVolume.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000015d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000005a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00003276
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000330c

```


Any ideas how to fix?

---

### Post by Pjotr123 on 2008-06-12
This how-to will do the trick, probably (second part, but do the first part as well, just to make sure):

First part:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Second part:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---


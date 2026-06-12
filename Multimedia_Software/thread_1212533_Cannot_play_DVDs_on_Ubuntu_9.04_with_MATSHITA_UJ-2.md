---
title: "Cannot play DVDs on Ubuntu 9.04 with MATSHITA UJ-220"
date: 2009-07-13
forum: Multimedia Software
---

### Post by Aaron44126 on 2009-07-13
Hi all,

DVD playback was working on my Ubuntu 9.04 system until recently, when I replaced the optical drive with another one from Dell under warranty replacement.  Now, I can only play unencrypted DVDs.

When I try to play DVDs, I just get a generic error about unable to read the disc.  Totem-xine asks me if I am trying to play an encrypted DVD without libdvdcss installed.

 - libdvdcss2 is installed, from Medibuntu.
 - According to the regionset tool, the region is set to Region 1, which is correct to play these discs.
 - My old drive and my new drive were both MATSHITA UJ-220 drives.
 - The DVD does show up on the desktop and I can browse the file structure.
 - I've tried several programs: totem, totem-xine, vlc, mplayer...  Even tried playing it in a virtual machine running Windows.

I've seen some other threads that mention that MATSHITA drives don't like to read a disc if the region is not set correctly.  But, as far as I can tell, the region is set.

Anyone have any ideas?

Following is the output from trying to open a disc in totem-xine.
```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: no file info
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000441
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000058c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002c01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00002c16
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00005ab6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0000fd59
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 1.1.16.3 from http://xine.sf.net
libdvdnav: DVD Title: CURIOUS_CASE_BEN_BUTTON_DOM
libdvdnav: DVD Serial Number: 3A728CC3
libdvdnav: DVD Title (Alternative): CURIOUS_CASE_BEN_BUTTON_DOM
libdvdnav: Unable to find map file '/home/aaron/.dvdnav/CURIOUS_CASE_BEN_BUTTON_DOM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
libdvdread: Using libdvdcss version 1.2.10 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000441
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004b1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000058c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002c01
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00002c16
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00005ab6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0000fd59
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Using dvdnav version 1.1.16.3 from http://xine.sf.net
libdvdnav: DVD Title: CURIOUS_CASE_BEN_BUTTON_DOM
libdvdnav: DVD Serial Number: 3A728CC3
libdvdnav: DVD Title (Alternative): CURIOUS_CASE_BEN_BUTTON_DOM
libdvdnav: Unable to find map file '/home/aaron/.dvdnav/CURIOUS_CASE_BEN_BUTTON_DOM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
```

---

### Post by igorzwx on 2009-07-13
Perhaps, something is missing.
Some codecs, or plugins.

This howto always work for me:
**[*Howto* make *Ubuntu 9.04* (Jaunty Jackalope) *Multimedia Ready* |Linux [B]...**]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")[/B]

22 Apr 2009 **...** *Howto* make *Ubuntu 9.04* (Jaunty Jackalope) *Multimedia Ready*. *Ubuntu 9.04* Required the foll0wing steps to Run *Multimedia* files like MP3, AVI, **...**
shibuvarkala.blogspot.com/.../**howto**-make-**ubuntu**-904-jaunty-jackalope.html -

---

### Post by Aaron44126 on 2009-07-13
> **igorzwx said:**
> Perhaps, something is missing.
Some codecs, or plugins.


Thanks, but I've checked to make sure that everything I need is installed.  And since it worked before I swapped my DVD drive out, I don't think that's a problem...

---

### Post by igorzwx on 2009-07-13
libdvdcss2 is not enough, xine plugs (all) might be needed

---

### Post by Aaron44126 on 2009-07-13
I already have all of the xine plug-in packages installed.

---

### Post by Aaron44126 on 2009-07-13
Some reinstalling packages and rebooting later, I get this when I try to play a DVD:

[IMG]http://stuff.aaron-kelley.net/2009/07/vlc-gunk.png[/IMG]

An improvement, I suppose, but not very helpful.  I can hear and see bits and pieces of the movie while this is playing.  (Yes, libdvdcss2 is installed.)

Any more ideas?

---

### Post by mc4man on 2009-07-13
try going into home folder and deleting the .dvdcss folder (hidden

---

### Post by igorzwx on 2009-07-14
In some new drives protection might be enabled.
Did it work with an old drive?
There are USB DVD drives, I have one.
Ask friends

---

### Post by Aaron44126 on 2009-07-14
Thanks, deleting the .dvdcss folder fixed it.
(I also got this advice on the VLC forum.)

---

### Post by davy jones on 2009-07-29
thanks a lot!!!

---


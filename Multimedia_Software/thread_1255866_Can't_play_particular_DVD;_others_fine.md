---
title: "Can't play particular DVD; others fine"
date: 2009-09-02
forum: Multimedia Software
---

### Post by ceo on 2009-09-02
I'm having a bizarre problem playing a particular DVD in Jaunty with totem-xine. All of the other DVDs in my (minuscule) collection play just fine, including the first disc in this two-disc set and the other two two-disc sets of this series. However, when I try to play the second disc in this set, I get "The source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

Answer: no, I effing well do have libdvdcss, as evidenced by my ability to play all my other encrypted DVDs just fine. More usefully, totem-xine tun from the command line gives me the following on startup:

```
ceo@talisker% totem-xine
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: no file info
libdvdnav: Using dvdnav version 1.1.16.3 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: RETURN_KING_EXT_D2
libdvdnav: DVD Serial Number: 313209c9
libdvdnav: DVD Title (Alternative): RETURN_KING_EXTENDED
libdvdnav: Unable to find map file '/home/ceo/.dvdnav/RETURN_KING_EXT_D2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001ab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000023f2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000631a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003b3104
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

```
When I go to play the disc, it repeats everything from "libdvdnav: Using dvdnav version 1.1.16.3..." onward.

Again, DVD playback works fine with every other disc I've tried. And, this disc works fine in my wife's Mac Mini (which also has a mini monitor, so I'd rather not use it for this). The disc in question is Disc 2 of *The Lord Of The Rings: The Return Of The King* Special Extended Edition, so you might guess that I'm finding this more than slightly frustrating. :-(
 
I tried mplayer, and it tries to play the disc, but the output is wildly pixellated and distorted. Once again, it works fine with other discs.

---

### Post by mc4man on 2009-09-02
You really shouldn't be having any issues with that disc, have the same one and plays fine in totem-xine (shows same output as you.

Try this
Go into the home folder (show hidden files) and locate the .dvdcss folder

Either delete the complete folder or open it up and look for a folder named this or very, very similar and delete it

RETURN_KING_EXT_D2-2004091718141900-2b36e4e9d7

Then try to play again

(if it still doesn't play then post back and I'll suggest a way or two for you to get the right keys in that folder

---

### Post by ceo on 2009-09-02
You, sir, are a hero of the revolution.

---


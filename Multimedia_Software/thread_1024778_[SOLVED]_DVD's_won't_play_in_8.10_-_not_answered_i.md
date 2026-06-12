---
title: "[SOLVED] DVD's won't play in 8.10 - not answered in other threads"
date: 2008-12-29
forum: Multimedia Software
---

### Post by phantomjoker on 2008-12-29
Yay, the joy that 8.10 has brought me....

Another annoying problem -


So dvd's will not play, and any movie player just exits just after clicking play.

This is the output
> libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: AMERICAN_DAD_V1_DISC1
libdvdnav: DVD Serial Number: 346D8D21
libdvdnav: DVD Title (Alternative): AMERICAN_DAD_V1_DISC1
libdvdnav: Unable to find map file '/home/mckenzie/.dvdnav/AMERICAN_DAD_V1_DISC1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
mckenzie@mckenzie-home:~$ 


I have the medibuntu packages
I have VLC

also
> 
mckenzie@mckenzie-home:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD


i also have 
libdvdread3, libdvdcss2, ubuntu-restricted-extras and libdvdnav4

I don't have the answer. Anyone?

---

### Post by phantomjoker on 2008-12-29
Solved!

Ok, for anyone reading this ----

open VLC, go to tool>preferences

then expand the video tab

for the output select X11

Done!

Make sure you have all the packages listed above, and also make sure you have a region set on your dvd player (use regionset)

ACE!

---

### Post by j@am1 on 2008-12-29
um...no. 
still does zilch.

---


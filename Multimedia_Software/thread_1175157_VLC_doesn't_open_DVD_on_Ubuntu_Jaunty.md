---
title: "VLC doesn't open DVD on Ubuntu Jaunty"
date: 2009-05-31
forum: Multimedia Software
---

### Post by miousername on 2009-05-31
When i try to open a dvd vlc gives this error:


[00000421] main access error: no access module matched "dvd"
[00000418] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/capo/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[00000424] main access error: no access module matched "dvd"
[00000422] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"
-------------------

suggestion??

---

### Post by Sub101 on 2009-05-31
Looks to me like you have not yet installed the restricted extras. This link should help:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---


---
title: "MythBuntu 12.04 &quot;Play Optical Disc&quot; won't play AudioCD"
date: 2012-11-27
forum: Mythbuntu
---

### Post by NoLedgeSeeker on 2012-11-27
This has got to be a config issue on my part. But i can't figure out what it is.

I put in a DVD... Myth finds it, the "Play Optical Disc" button plays it.

But, I put in an AudioCD...  No!

I know it's there, Myth can obviously read it because the "Import CD" button is happy to rip it. But... the "Play Optical Disc" button does _nothing_.

VLC is happy to play it.

The system has my drive located at /dev/sr0.  I've changed Myth's locations to point to /dev/sr0 and, just in case i've missed something, i've also created a sym link /dev/cdrom -> sr0. The permissions on sr0 are brw-rw-rw-+.

What am i doing wrong ?
:confused:

---

### Post by brainstream on 2012-12-06
I have the exact same issue with Mythbuntu 12.04. The console is saying this when i try to play a music CD:

```
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2012-12-06 16:09:20.652861 E  DVDInfo: Failed to open device at /dev/sr0
```

It seems to me like it's trying to play the CD as a DVD. Does this "Play Optical Disc" option realy play music CD's?

---


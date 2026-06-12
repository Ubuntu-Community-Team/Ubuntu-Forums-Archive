---
title: "&quot;iTunes&quot; AAC / Pioneer head unit"
date: 2008-10-03
forum: Multimedia Software
---

### Post by awry on 2008-10-03
I just got a new Pioneer head unit for my car (P6000UB).  It's pretty sweet.  It has USB mass storage support, so you can plug in any USB device with mp3, wma, or aac files, and it has convenient navigation.

Anyway, the manual specifies:
> AAC decoding format: MPEG-4 AAC (iTunes encoded only) (.m4a) (Ver. 7.2 and earlier)

I can't seem to get any of my FAAC encoded AAC files to play.  At first I thought "iTunes encoded" might simply mean ABR instead of VBR, but that alone was not enough to make it work.

Anyone have any idea what's special about iTunes AAC encoding, and/or how to emulate it in FAAC so that I can encode in linux?  Don't tell me to run iTunes in wine either.  Not having it.

---

### Post by awry on 2008-10-03
Hmm, new clue.  On my faac encoded file, mplayer reports "ISO: File Type Major Brand: ISO/IEC 14496-1 (MPEG-4 system) v2" whereas mplayer reports "ISO: File Type Major Brand: Apple iTunes AAC-LC Audio" for iTunes-encoded AAC.  Hmm.

---


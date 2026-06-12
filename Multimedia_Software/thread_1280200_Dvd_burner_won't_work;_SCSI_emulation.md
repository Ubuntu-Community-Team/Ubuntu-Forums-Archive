---
title: "Dvd burner won't work; SCSI emulation?"
date: 2009-10-01
forum: Multimedia Software
---

### Post by onespeedbiker on 2009-10-01
My dvd burner is now erroring out saying the blank dvd's need more space.  The last time this happened I continually tried to burn a dvd until suddenly the /media/ window popped up and everything reverted back to normal. Whatever this problem, it stops using the media/cdrom/ directory to burn and view videos. Previously when I started a video it ran from "cdrom"; now it is running from a directory it creates called "DVD" when it mounts. The result is I can not burn any dvds while it's in this mode. The last time it happened I continually tried to burn a dvd until suddenly the /media/ window popped up and it started running in normal mode again. This happened the last time I had a major update. So far I have been unable to jolt unbuntu back to normal so my dvd burner is dead. Is there any fix for this.

here is one of the errors:

brad@brad-desktop:~$ growisofs -Z /dev/scd1 -dvd-video dvd/
Executing 'genisoimage -dvd-video dvd/ | builtin_dd of=/dev/scd1 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
:-( /dev/scd1: 2295104 blocks are free, 2378323 to be written!
:-( write failed: No space

---


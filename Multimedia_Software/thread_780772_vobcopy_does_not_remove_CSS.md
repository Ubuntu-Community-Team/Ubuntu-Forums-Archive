---
title: "vobcopy does not remove CSS?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by incandenza on 2008-05-03
I'm trying to rip CSS-protected DVDs using "vobcopy -m".  (Also tried dvdbackup, which seems to be the same.)

It seems that the resulting files do not have the CSS removed.  I do have libdvdcss2 installed, and I can play the CSS-protected discs normally from the original disc.  But when I try to play the vobcopy rip with VLC, it will play the menus and promo material but not the movie itself.

Is there something I need to do to make this work?  All the guides I read seem to say that the CSS is removed automatically.

Maybe a more complex package like dvd::rip would work, but all I want to do is rip the contents of the disc, not convert it to any other format.

Thanks for any help.

---

### Post by mc4man on 2008-05-03
I use vobcopy for most everything, should be removing css, use this command and ck. output. (ver. 1.02, 1.10 and 1.11 are better than gutsy ver.)
```
vobcopy -v -m /media/cdrom0
```   (adjust if needed for mount point) , if you have later versions use 
```
vobcopy -v -m -F 16 /media/cdrom0
```
note: this rips to home directory, if you want to specify, ex. to a mounted partition  ```
vobcopy -v -m -o /media/rips -F 16 /media/cdrom0
```

---

### Post by incandenza on 2008-05-03
Thanks for the reply.  I'm not doing anything differently than you describe, but I'm pretty sure it's not ripping the CSS.  I'll try to attach the output below.

e.g., if I just play the disc in VLC, I see a bunch of lines from libdvdread about how it's grabbing the CSS keys.  But from vobcopy I see nothing like that.

I included both the vobcopy and the vlc output for comparison.

---

### Post by incandenza on 2008-05-03
Ah, OK, never mind, I think it was something having to do with the particular disc I was trying to rip.  There's something weird about the menus which causes it to hang even playing from the native disc.  A different disc worked fine.

---

### Post by mc4man on 2008-05-03
there won't be any mention of css, keys ect., if it's ripping then it's being decrypted. Probably 99% of titles will rip and playback fine. Occasionally you may need to fix the dvd structure for proper navigation, usually on disks with structure protection, sometimes on ones without. You'll know if structure protection is present if you see this
```
Writing to /media/lose/<clipped>/VIDEO_TS/VTS_01_1.VOB 
[Warn] Had to skip 0 blocks!  [Warn] Had to skip 1 blocks!  [Warn] Had to skip 2 blocks!  [Warn] Had to skip 3 blocks!  [Warn] Had to skip 4 blocks! 
``` (will also show up when disk is damaged, but more at random) 
If you have means to fix disk structure then vobcopy (with a modified source) is good for structure protected disks where the number of unreadable sectors is 5000 or less, any more isn't worth the time and drive wear and tear.

---


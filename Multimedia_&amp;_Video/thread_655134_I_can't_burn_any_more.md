---
title: "I can't burn any more"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by jtgd on 2008-01-01
I have been successfully burning ISO's for a long time, but suddenly I
can't.  I wonder if some recent software update may have broken
something.

The message from Gnomebaker v0.6.0 is:

[INDENT]Executing 'builtin_dd if=/Video/DVD/my.iso of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 8.2x1352KBps.
: -? the LUN appears to be stuck writing LBA=10h, keep retrying in 92ms
: -[ WRITE@LBA=10h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
: -( write failed: Input/output error
/dev/hda: flushing cache
/dev/hda: updating RMA
/dev/hda: closing disc
[/INDENT]

The "LUN appears to be stuck" message I've been getting before even
with successful burns.  The subsequent two messages are new.

I get the same problem with K3b 1.0.3 (I believe they are both just
front-ends for genisoimage).

I have tried at 8x and 4x, with TDK and Taiyo-Yuden media, dusted the
lens with a Memorex cleaning disc, and tried a cold reboot to reset
the drive.  

I'm running Kubuntu Feisty 64bit on dual Opteron w/4GB using a Plextor
PX-760A which is less than a year old and has been burning fine until
now.  My only idea left is to swap out with my older Pioneer 110D.

Does anybody have any ideas?

---

### Post by foxmulder881 on 2008-01-01
> **jtgd said:**
> I have been successfully burning ISO's for a long time, but suddenly I
can't.  I wonder if some recent software update may have broken
something.

The message from Gnomebaker v0.6.0 is:

[INDENT]Executing 'builtin_dd if=/Video/DVD/my.iso of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 8.2x1352KBps.
: -? the LUN appears to be stuck writing LBA=10h, keep retrying in 92ms
: -[ WRITE@LBA=10h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
: -( write failed: Input/output error
/dev/hda: flushing cache
/dev/hda: updating RMA
/dev/hda: closing disc
[/INDENT]

The "LUN appears to be stuck" message I've been getting before even
with successful burns.  The subsequent two messages are new.

I get the same problem with K3b 1.0.3 (I believe they are both just
front-ends for genisoimage).

I have tried at 8x and 4x, with TDK and Taiyo-Yuden media, dusted the
lens with a Memorex cleaning disc, and tried a cold reboot to reset
the drive.  

I'm running Kubuntu Feisty 64bit on dual Opteron w/4GB using a Plextor
PX-760A which is less than a year old and has been burning fine until
now.  My only idea left is to swap out with my older Pioneer 110D.

Does anybody have any ideas?


First off, I don't think Gnomebaker and K3b are different front-ends for the same workings. Someone correct me if I'm wrong, but from what I was aware, the use totally different libraries.
Gnomebaker being developed for the Gnome GUI and K3b for the KDE GUI.

Anyway, back to the real issue here...
If you have the same problem with different burning applications and for different media, then I'd suggest that you have a problem with the writer itself.
Try another writer and post the results.

---

### Post by jtgd on 2008-01-06
Not a software problem.  The drive was bad.

The Plextor failed the self-test.  I swapped with the Pioneer and it works fine.

---

### Post by foxmulder881 on 2008-01-07
I suspected so. Thanks for the update.

---


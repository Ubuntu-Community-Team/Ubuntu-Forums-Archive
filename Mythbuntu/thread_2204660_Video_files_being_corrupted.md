---
title: "Video files being corrupted"
date: 2014-02-09
forum: Mythbuntu
---

### Post by craig8 on 2014-02-09
Hello all,
I've just taken the plunge into Mythtv.  I'm running Ubuntu 12.04.4 with Mythtv 2:0.25.2.  All of my media is stored on a 2TB EXT4 filesystem on a drobo.  It seems that periodically all the videos are being corrupted, as in videos I have been able to play, no longer work.  These are videos that I have downloaded.  Luckily I have a copy of most of my videos on an NTFS partition on my drobo, but these are not effected, but I'm not sure if this is because it is on NTFS or that it is not defined in MythTV.  Can someone please help me.

Regards
Craig Murray

---

### Post by aelfric55 on 2014-02-11
> **craig8 said:**
> Hello all,
I've just taken the plunge into Mythtv.  I'm running Ubuntu 12.04.4 with Mythtv 2:0.25.2.  All of my media is stored on a 2TB EXT4 filesystem on a drobo.  It seems that periodically all the videos are being corrupted, as in videos I have been able to play, no longer work.  These are videos that I have downloaded.  Luckily I have a copy of most of my videos on an NTFS partition on my drobo, but these are not effected, but I'm not sure if this is because it is on NTFS or that it is not defined in MythTV.  Can someone please help me.

Regards
Craig Murray

It would be really surprising if all media stored on an external drive spontaneously corrupted, without there being a mechanical/electrical  issue with the drive or some event causing massive damage to the filesystem on that drive, like a significant power surge or a series of dirty shutdowns. Ext4 filesystems are usually very hardy beasts.

So first confirm that the media files are in fact corrupted. Can the "corrupt" .mpg (or other) files be found and played directly from the Ubuntu desktop using any of the variety of standalone players that one uses for this --VLC, Xine, Mplayer, etc. ? If  these "corrupted" .mpg files can be found and played from the desktop with a standalone player, then the issue is not corruption, nor mechanical or filesystem problems on the drive, nor communication between the Motherboard/OS and the drive. At that point suspicion would shift to the Mythtv installation itself, and you'd start looking at what's going on in the backend and frontend logs at the point where mythtv tries to access the affected videos.

If, however, the videos can't be found in the filesystem at all, or accessed, or played by anything from the desktop, then the issue is more fundamental than a mythtv thing, and troubleshooting should proceed to the drive, filesystem, communication, and OS possibilities.

---

### Post by craig8 on 2014-02-11
Thanks for the reply.  After a bit more research, it turns out that drobos advice of treating it as a SCSI drive is incorrect, as after a bit more research, it turns out that drobo do not support ext4, and for my model, all volumes on the drobo must have the same filesystem type, which for me unfortunately means NTFS. :(

---


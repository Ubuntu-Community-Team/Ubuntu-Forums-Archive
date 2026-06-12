---
title: "Sansa Clip+ MTP Issues"
date: 2009-12-25
forum: Multimedia Software
---

### Post by Mr_Mischif on 2009-12-25
I picked up a 8G Sansa Clip+ for Christmas, but I can't seem to make it work under MTP. I've been trying other media players to see if it's just Rhythmbox, but no dice. Right now I've just got it in MSC mode with an .is_audio_player file to at the very least show up *somewhere*, but it won't make the podcast files go in the podcast folder. Does anyone have any suggestions?

P.S. I'm running Karmic.

---

### Post by saturnine fei on 2009-12-26
I am in the process of seeing if I can migrate from 8.4 to 9.10 and was having a problem with my 4 gig sansa clip.  It was not recognized.  I found on another web site that I had to change the USB setting (I never knew there was such a thing) to MSC (it was in auto detect when I found the setting) and now it works fine.  I did have to change the location of the device in gpodder.  It used to show up as /media/disk but in 9.10 it seems that my USB Drives and this device show up as /media/####-####.  where # = a digit.  I have not seen this naming convention before and do not know what the numbers are, but it seems to be working fine once I told my application (gpodder) where to look for the device.

---

### Post by fperwth on 2009-12-30
After compiling the latest CVS/SVN versions of *libmtp*
[http://libmtp.sourceforge.net/download.php](http://libmtp.sourceforge.net/download.php)
and [I]mtpfs
[/I][http://code.google.com/p/mtpfs/source/checkout](http://code.google.com/p/mtpfs/source/checkout)
(remove the Ubuntu packages before), I was able to access my Sansa Clip+ via MTP with Amarok.

---


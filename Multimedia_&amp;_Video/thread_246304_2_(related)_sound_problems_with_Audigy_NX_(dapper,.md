---
title: "2 (related?) sound problems with Audigy NX (dapper, dell d610)"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by aschiller on 2006-08-29
I've been having a dream experience with Dapper on my Dell D610.  The only problem I have is with sound.  The internal sound card is a Sigmatel STAC9750.  It works just fine on its own, but it is not capable of producing any quality sounds.  Enter my Audigy NX usb.

1) If I login with the Audigy NX plugged in, it works--to an extent.  It will only play one source at a time, so if rhythmbox is playing music, gaim will not produce sounds.  I've tried a variety of applications, and this behavior is consistent.

2) When I suspend-to-RAM and wake the computer back up, the NX simply won't play anything.  (If I unplug it, I can get sound out of the internal card).  When I unplug and replug it, dmesg and lsusb respond as expected (recognizing the device, etc), but it will not play any sounds until I log out and log in to a new GNOME session.

I imagine the problem is in ALSA.  I know very little about ALSA, which is why I haven't included any diagnostic printouts; if someone would offer a quick primer and locations of relevant configs and programs, I would really appreciate it.  I would ultimately like to throw together a fast alsa-reset script to run on wake from suspend.

Thanks.

---


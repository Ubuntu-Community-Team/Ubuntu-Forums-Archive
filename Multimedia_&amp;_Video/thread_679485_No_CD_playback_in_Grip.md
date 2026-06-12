---
title: "No CD playback in Grip"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by cneil on 2008-01-27
Hello,
I am using Grip 3.3.1 and Ubuntu 7.10 and CD playback doesn't seem to be working correctly.  Everything else seems to work.  It will download the CD information, rip tracks to a directory, and the CD light comes on so I know it is reading the disc.  I've adjusted all of the volume controls.  I've followed some other advice on the forum and adjusted my CD device from dev/cdrom to dev/hdc.  It doesn't seem to be outputting any error messages either.  
By the way, sound juicer seems to work perfectly.
Thanks.

---

### Post by logos34 on 2008-01-27
grip is bit archaic in this regard--it outputs CD playback as analog sound, so if you want hear anything you need to have a separate audio cable connecting the cdrom and soundcard/motherboard.

---

### Post by cneil on 2008-01-28
I have a Gateway 7510GX laptop.  This may not be possible.  Do you have any ideas?
Thanks,
-Cullen

---

### Post by logos34 on 2008-01-28
Use one of your media players, like Rhythmbox or something.  Or use gnome-cd

sudo apt-get install gnome-media

---


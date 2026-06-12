---
title: "Latitude D830 / Intel HDA sound not working - Gutsy"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by undoIT on 2007-10-20
Out of the box the Intel HDA sound card does not work and driver is not installed. I searched around for a way to fix this and found this:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I used method G since it was easiest and also reported to be most compatible. Initially after installing the backports the sound worked. Then something happened and there is no more sound. Uninstalling and reinstalling backports does not fix it. One of these might have caused it.

1. Suspend / Hibernate. Although this isn't reported to be a problem with method G, it might have broken the sound.

2. Updates - I applied some system updates.

3. I tried to play an MP3 in Amarok. It downloaded a bunch of packages to install MP3 support and that is when I first noticed that sound wasn't working anymore.

I have not tried compiling the Linux kernel or installing the Also 1.0.15 driver from source. Anyhow. I'm considering backing up the system and starting with a fresh install since it was working with Method G in the wiki. But that might not be worth it if the sound is just going to break again. Any suggestions?

---

### Post by philpinch on 2008-01-16
What deal is the best?
Method G or this?

[INDENT]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa[/INDENT]

This works great with Audacious, rhythmbox, vlc or RealPlayer.... 

But I can't record any sound.

---


---
title: "X-Fi - works in virtualbox?"
date: 2009-11-09
forum: Multimedia Software
---

### Post by berwynnn on 2009-11-09
I've been getting no sound out of my X-Fi pci-express in either 9.04 or 9.10.  I've done a number of clean installs, and all the number of guides and threads that I've read online haven't fixed the issue.

So maybe this isn't really a solution... (disclaimer: I use linux at work - but I don't know it or Virtualbox well enough to know whether the following makes any sense), but I did get it to work yesterday in VirtualBox in Win7.  It is a basic regular install in Virtualbox (using all the default/regular settings?), and after it rebooted after the install, it made the bu-bump intro sound on the login screen.  Sound was working just fine.  The X-fi doesn't show up in the "sound preferences" window - rather it says "Internal Audio Analog Stereo" under the Output tab, and simply "Internal Audio" under hardware - but I could really care less at this point so long as it's working.

(On the other hand, in all the usual installs of Ubuntu not using Virtualbox, any audio file just hangs after a second of playback.)

So, I was wondering why this would be the case, if it's working only because it's running inside Win7?, but if not, if it would be possible to replicate this in a native install.

If it's useful, another piece of info is that in the main window of Virtualbox, it says
Audio Host Driver: Windows DirectSound
Controller: ICH AC97

Anyone got any ideas?  It would be great to have *any* sound in Ubuntu at this point...

---

### Post by kostkon on 2009-11-10
It should/may work on 9.10. Try installing the
```
linux-backports-modules-alsa-karmic-generic
```
package and reboot.

---

### Post by berwynnn on 2009-11-10
thanks for the reply.  i will be able to try it out later today and will see what happens.

---

### Post by berwynnn on 2009-11-10
i ran sudo apt-get install on the package, and rebooted, but everything seems the same.  the sound preferences looks the same as well (only the sb x-fi xtreme audio is listed).  is there a step that i'm missing?

---

### Post by berwynnn on 2009-11-11
hm...no response...i thought that getting the x-fi to work was a problem that other users had as well.

giving the post one more bump.

---


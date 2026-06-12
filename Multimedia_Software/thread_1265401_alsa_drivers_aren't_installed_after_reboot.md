---
title: "alsa drivers aren't installed after reboot"
date: 2009-09-13
forum: Multimedia Software
---

### Post by xxxYYY on 2009-09-13
Hi,
After going through some of the exercises posted on this web page, I can get sound going, however, right now I have to re-install (see below) after rebooting each time.

Without the reinstall, sudo modprobe gives a slew of errors, e.g.
> sudo modprobe snd-emu10k1
FATAL: Error inserting snd (/lib/modules/2.6.24-24-server/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-24-server/updates/alsa/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_util_mem (/lib/modules/2.6.24-24-server/updates/alsa/synth/snd-util-mem.ko): Unknown symbol in module
...

I don't really want to go through some of the "purge" instructions 
(posted here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), because not only does it remove the gdm desktop, it removes the kde desktop, and mine is OK but still isn't quite back to the way it was.  I sort of regard this as a bug that should be fixed.


This gets sound going:

> sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

> sudo modprobe snd-emu10k1


The question is, what do I need to fix to get sound to come up after reboot?:confused:

Thanks

---


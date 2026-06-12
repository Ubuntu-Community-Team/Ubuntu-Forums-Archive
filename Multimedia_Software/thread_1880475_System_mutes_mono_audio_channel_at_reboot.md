---
title: "System mutes mono audio channel at reboot"
date: 2011-11-13
forum: Multimedia Software
---

### Post by VictorMature on 2011-11-13
32bit Xubuntu 11.10.  This is an IBM Thinkcentre with an internal mono speaker and a stereo output jack.  Lspci identifies the hardware as 00:1f.5 Multimedia Audio Controller: Intel Corporation 8201EB/ER (ICH5/ICH5R)

I don't have speakers hooked up to the jack, I just want to use the internal speaker.  It is on the "Master Mono" channel in alsamixer.

Whenever I reboot, the mute switch on this channel gets enabled and the output gets set to 0.  The other setting are not affected.

Wondering if there is a configuration file I can edit to force this channel on?

I tried running alsamixer as root, and as regular user.

---

### Post by Toz on 2011-11-14
I know the thread is a little dated, but see: [http://ubuntuforums.org/showthread.php?t=764576]("http://ubuntuforums.org/showthread.php?t=764576") - especially the instructions in post #5 as a workaround. Its interesting that this isn't being done automatically for you.

---

### Post by VictorMature on 2011-11-14
Thanks a bunch.  This worked out.  It is weird though.  When I examined the file /var/lib/alsa/asound.state, the correct values were in there.  So, it doesn't look like a write permission problem.  It is almost as if this driver has been tweaked to load with the onboard sound muted.

---


---
title: "mceusb remote, suspend/resume and lircd"
date: 2009-01-31
forum: Multimedia Software
---

### Post by desht on 2009-01-31
Hi all,

I know there's been a few posts on this topic, but my case seems a little different... I have a D945GCLF2 motherboard and a mceusb2 remote.  I have suspend/resume working, and the remote is detected and works nicely with lirc, using irexec, mythtv & mplayer.  This is all on an Intrepid system using standard packages.

The systems suspends fine if I run "pm-suspend" from irexec (when I press the power button on my remote).  It comes back up fine when I press the power button again (I've configured /proc/acpi/wakeup to pick up USB activity), with everything as I left it, except...

For some reason the lirc device changes.  Before suspend I have /dev/lirc0, and lircd is reading that.  After the resume I have /dev/lirc1, and lircd has exited since the device it was reading has gone away.

Now I can always restart lircd & irexec via a /etc/pm/sleep.d script, but this is far from ideal - mythfrontend won't pick up the newly restarted lircd, so the WAF is pretty poor :)  I don't want to have to restart mythfrontend every time I suspend/resume.

So I guess the real question is why is the lirc device changing on suspend/resume?

---

### Post by rgsteele on 2009-02-11
I think I'm seeing the same issue. I've got an ASUS P5E-VM HDMI motherboard with the mceusb2 remote. I haven't set up irexec or /proc/acpi/wakeup to suspend or resume the computer yet, but when I do it manually I encounter the same issue... /dev/lirc0 is replaced by /dev/lirc1. Then if I suspend and resume again, I've got /dev/lirc0 again.

I don't have a wife, so it's not as urgent for me, but it would still be nice to have fixed :)

---

### Post by jis on 2009-10-31
Bump.

I have VLSystem MPlay Blast remote. When I resume from suspend, device name has changed from /dev/ttyUSB0 to /dev/ttyUSB1, lircd is taking a lot of CPU and also VLC takes excessive amount of CPU, if it was started using the lirc control interface. This is in Jaunty. In Karmic I couldn't get the remote work at all.

Line > REMOTE_DEVICE="/dev/ttyUSB0" had to be added to /etc/lirc/hardware.conf to make lircd work with the remote initially.

---

### Post by pashdown on 2009-12-31
I have just run into this very problem.  If anyone has a fix, please let us know!

---

### Post by rgsteele on 2010-01-13
This was fixed in Karmic. If you don't want to upgrade, I've posted the fix to the bug report here:

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/387443](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/387443)

You may want to subscribe and mark this bug as affecting you. If enough people report the issue, it could be a candidate for an SRU.

---


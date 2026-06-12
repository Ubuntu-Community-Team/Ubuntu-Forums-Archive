---
title: "ALSA failure, no sound card, proc/asound/modules &quot;no such file or directory&quot;"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by jasc on 2007-09-25
Lenovo 3000 C200

karyn@ubuntu:~$ cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory

I received an output similar to this guy's [https://bugs.launchpad.net/baltix/+bug/43961/comments/220](https://bugs.launchpad.net/baltix/+bug/43961/comments/220)

ALSA just stopped working. I had to recompile ALSA with a realtek6 patch to get it to work, originally, and its been fine up till now. It just stopped working. 

Double clicking on the inexplicably muted volume control returns this message: "No volume control Gstreamer plugins and/or devices found"

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 3802
        Flags: fast devsel, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


I have no idea what's wrong. Please help!

---


---
title: "No sound in applications, sound OK in System Settings"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Lars Noodén on 2010-07-27
All of the sound tests (notifications, music, video, communications, games, accessibility) in KDE's System Settings utility play sound on internal, external and headphones for me.  *KDE System Settings, Multimedia plays sound just fine* so I know the components are there and working.  

However, no actual applications (Amarok, Audacity, and so on) are actually able to play sound.  

What needs to be done to get the applications to play back properly?

$ lsb_release -rd
Description:    Ubuntu 10.04.1 LTS
Release:        10.04

$ uname -a Linux box 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

$ sudo modprobe snd-hda-intel
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.


And from lspci:

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
        Subsystem: nVidia Corporation Device cb79
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at d3480000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---


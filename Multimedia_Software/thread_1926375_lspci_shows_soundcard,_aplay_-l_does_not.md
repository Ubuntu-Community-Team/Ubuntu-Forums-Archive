---
title: "lspci shows soundcard, aplay -l does not"
date: 2012-02-16
forum: Multimedia Software
---

### Post by montitan on 2012-02-16
Hello,
Some details:

Asus E35M1-I motherboard with integrated AMD E-350 processor
Ubuntu Oneiric, Kernel 3.0.0

Output of lspci -v:
```
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
    Subsystem: ASUSTeK Computer Inc. Device 84a5
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

...

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 848d
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```so my idea was that the first one must (obviously) be the hdmi-device and the second would be the one for the 3.5mm plugs. However, aplay -l does not list anything.

The computer is running headless and i wanted to use it as a soundserver with mpd and an appropriate app for android.

Any ideas? Thx

---

### Post by montitan on 2012-02-16
I tried to get pulesaudio running which gave me following error:
```
Unable to contact D-Bus:
org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
```after some research i found _[COLOR=Black][this]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/812940")[/COLOR]_ post, which basicly says that with change to oneiric the dbus is not working if you don't have an xserver installed. could that be the problem? How could i fix it?

---


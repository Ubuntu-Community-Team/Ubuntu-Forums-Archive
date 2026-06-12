---
title: "Another lack-of-sound problem with HP-Intel"
date: 2009-07-03
forum: Multimedia Software
---

### Post by Darkness Falls on 2009-07-03
Looking around the boards, this problem doesn't appear to be anything new, but having tried some of the solutions on the sticky thread, I seem to have only succeeded in confusing myself, so I figured I'd ask in a new thread and try and get some help with it.

I'm new to Ubuntu and GNU/Linux in gerenal, and, on getting a new laptop, figured I wanted to make the break from Windows. I'm running 9.04 Jaunty dual-booting with Vista on an HP Pavilion dv7-2045ea (I've downloaded the backports modules, and updated the kernel about 3 weeks ago, so it should be relatively fresh), and I've been slowly learning how everything works.

The problem is, of course, there's no sound under Ubuntu. It works fine under Vista, but nothing plays sound in Ubuntu, not even the example files that came with the distro. This seems to be a relatively common issue, so I tried reading some of the threads about it here - unfortunately, my last attempt at editing the *alsa-base.conf* file ended up in me making a change that caused Ubuntu to hang on boot-up. I've managed to fix the problem by booting from the CD and undoing the change, but as it's clear I don't really understand what I'm doing, I'm kind of reluctant to fiddle with it further without a bit of help.

The following, then, is a list of the outputs from various commands, as recommended in the Comprehensive Sound Problem Solutions Guide thread. The *aplay -l* command gives the following:

```
*** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

I don't understand why the numbering system skips from device 1 to device 3 like that, but I don't know if that's relevant or not.

Next, *lspci -v*. This gives a lot of information about all sorts of things; the bits dealing with audio devices read thusly:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Subsystem: Hewlett-Packard Company Device 3063
Flags: bus master, slow devsel, latency 64, IRQ 16
Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

((a bit later on))

01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
Flags: bus maser, fast devsel, latency 0, IRQ 19
Memory at d2310000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
```

I'm a little concerned about that "<access denied>" line, but it appears in the listings for other things as well (the graphics card, the network controller, etc.) and they all seem to work fine, so again, I don't know if that's relevant or not.

I've gone into Alsamixer and unmuted all the channels and set them to maximum, and I've checked that my username is part of the /etc/ group. I then read that the *alsa-base.conf* file can be modified with additional lines to help Ubuntu recognise specific sound cards, but that HP-Intel is particularly awkward to do this with as it has lots of different permutations, some of which were designed to work with Toshiba chipsets and such, and there was nothing listed as a suggestion for the Pavilion dv7-2045ea. I tried a couple of the others, but that was what led to the hanging-during-boot-up problem.

Has anyone else had any success with this, or have any recommendations?

D.F.

---

### Post by Darkness Falls on 2009-07-05
Just bumping this in hopes of a reply. I can provide more information if needed.

Anyone?

D.F.

---


---
title: "Hda-Intel card - doesn't seem to do anything"
date: 2008-11-01
forum: Multimedia Software
---

### Post by soluphobe on 2008-11-01
Hi,

I've got a new Ubuntu system.  I managed to get the graphics card working, but sound is eluding me.  I tried to follow the comprehensive instruction guide, but I think I might have messed up, because it just didn't work.  To elaborate, this card only plays noise under Windows (which crashed and had to be wiped, so I don't have it anymore) and the Bios.  Under Ubuntu, it seems to show up but doesn't do anything.

Note: Every OS I've run on this machine has been 32-bit, yet all commands (for example lshw) say my sound system has a 64-bit width.  Should I go for 64-bit ubuntu?
(my wifi card also says 64-bit, and that has issues too, though I know how to fix it once I upgrade to Ibex)

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ sudo lspci -v | less
...
00:1b.0 Audio device: Intel Corporation 820801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 11c3
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f9ff8000 (64-bit, non prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
...
```

That's what I saw as I was following the guide.  So I went to the Alsa-project website, but they must have redesigned because I couldn't find any dropdown boxes.  I searched around on their wiki for a while, and hda-intel should be supported (right?).

I thought perhaps it was muted, so I went to the deskbar applet and maxed everything.  But everything was still silent.  So I ran alsamixer, and I got a depressing screenshot (see attatchement).  It doesn't show whether anything's muted or not - which makes me worry that the drivers even exist.

I've modprobe'd snd-hda-intel, and that doesn't solve anything.  Am I doing something wrong?  Are there some specific kernal packages I should install?

---


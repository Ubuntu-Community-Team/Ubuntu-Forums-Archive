---
title: "sound config issue with P5LD2"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by gunghoiguana on 2007-04-10
I just installed Edgy Eft on a machine with a P5LD2 mainboard, which has sound built in.  It's saying there are no sound devices.  The good news is that lspci finds it:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8237
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at cdcf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

Sure enough, it's there in /dev/snd, and asoundconf sees it:

$ls /dev/snd
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  pcmC0D2c  timer

$asoundconf list
Names of available sound cards:
Intel

But I have no sound, and the volume control says there's no sound device.  What am I missing?

Thanks for any help!

---


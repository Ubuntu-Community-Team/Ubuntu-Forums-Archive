---
title: "Mic/Line In Not Working Very Well"
date: 2009-03-01
forum: Multimedia Software
---

### Post by pkulak on 2009-03-01
I'm getting a bunch of popping and hissing and bad stuff through both line in and mic. My board is the "ASRock 775Dual-VSTA LGA 775 VIA PT880 PRO ATX", which has the VIA VT8237A chipset, which according to [this]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA") means I need the snd-hda-intel module. When I do a lsmod | grep snd_hda_intel it turns up three lines. However, when I do aplay -l, I get "no soundcards found...". Could this be my problem? And if so, I have no idea what to do about it. Thanks for any help!

---

### Post by pkulak on 2009-03-02
Also, if I run lspci -v I get this:

```

02:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: ASRock Incorporation Device 0888
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

So that looks fine too.

---


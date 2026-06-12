---
title: "Terrible Video Performance (13.10)"
date: 2014-02-15
forum: Multimedia Software
---

### Post by scambro on 2014-02-15
I just installed 13.10 on a new server, desktop version.  I say new, only because it's new to me.  The motherboard is a bit old, but it was cheap.  It is going to act as a server for me, but I need X on it because I plan on running some VMs inside.  In other words, it doesn't have to be great, but it has to be passable.  The specs of the box seem good enough that they should be running this without a problem, but the video performance is so terrible, that as I type right now I get a solid 5-7 second delay between hitting a key and it showing on the screen.  The same delay is noticed when I drag something on the screen.  Oddly enough, if I move the mouse, the reaction seems pretty normal (there's no pointer lag until I drag something.

```
$ lspci -nn | grep VGA
07:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] ES1000 [1002:515e] (rev 02)

```

I know that's not exactly a blazing video card, but it should be able to handle a desktop system.

```
$ dmesg | egrep 'drm|radeon'
[   12.480093] [drm] Initialized drm 1.1.0 20060810
[   13.950633] [drm] radeon kernel modesetting enabled.
[   13.950946] [drm] initializing kernel modesetting (RV100 0x1002:0x515E 0x15D9:0x8680).
[   13.950966] [drm] register mmio base: 0xD8200000
[   13.950967] [drm] register mmio size: 65536
[   13.951055] radeon 0000:07:01.0: VRAM: 128M 0x00000000D0000000 - 0x00000000D7FFFFFF (16M used)
[   13.951057] radeon 0000:07:01.0: GTT: 512M 0x00000000B0000000 - 0x00000000CFFFFFFF
[   13.951060] [drm] Detected VRAM RAM=128M, BAR=128M
[   13.951062] [drm] RAM width 16bits DDR
[   13.951147] [drm] radeon: 16M of VRAM memory ready
[   13.951149] [drm] radeon: 512M of GTT memory ready.
[   13.951160] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.972349] [drm] PCI GART of 512M enabled (table at 0x0000000036880000).
[   13.972368] radeon 0000:07:01.0: WB disabled
[   13.972371] radeon 0000:07:01.0: fence driver on ring 0 use gpu addr 0x00000000b0000000 and cpu addr 0xffff880036845000
[   13.972373] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.972374] [drm] Driver supports precise vblank timestamp query.
[   13.972383] [drm] radeon: irq initialized.
[   13.972393] [drm] Loading R100 Microcode
[   14.270794] [drm] radeon: ring at 0x00000000B0001000
[   14.270823] [drm] ring test succeeded in 1 usecs
[   14.271289] [drm] ib test succeeded in 0 usecs
[   14.271479] [drm] No TV DAC info found in BIOS
[   14.271502] [drm] Radeon Display Connectors
[   14.271503] [drm] Connector 0:
[   14.271505] [drm]   VGA-1
[   14.271506] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   14.271507] [drm]   Encoders:
[   14.271509] [drm]     CRT1: INTERNAL_DAC1
[   14.271510] [drm] Connector 1:
[   14.271511] [drm]   DVI-I-1
[   14.271512] [drm]   HPD2
[   14.271513] [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
[   14.271514] [drm]   Encoders:
[   14.271515] [drm]     CRT2: INTERNAL_DAC2
[   14.271516] [drm]     DFP2: INTERNAL_DVO1
[   14.307363] [drm] fb mappable at 0xD0040000
[   14.307365] [drm] vram apper at 0xD0000000
[   14.307366] [drm] size 786432
[   14.307367] [drm] fb depth is 8
[   14.307368] [drm]    pitch is 1024
[   14.307446] fbcon: radeondrmfb (fb0) is primary device
[   14.464167] radeon 0000:07:01.0: fb0: radeondrmfb frame buffer device
[   14.464169] radeon 0000:07:01.0: registered panic notifier
[   14.464174] [drm] Initialized radeon 2.34.0 20080528 for 0000:07:01.0 on minor 0
```

Any ideas?  If I try to fire up one of my VDIs the performance inside the VDI is to the point where I can't use a mouse because it's so unpredictable.  Is this video card (built into the motherboard), really THAT bad?

Thanks!

---

### Post by Yellow Pasque on 2014-02-15
Try running a non-3D desktop environment (like xfce or lxde). The ES1000 is basically a cut down version of the original Radeon with very limited 3D power. It's no surprise that Unity brings it to its knees.

---

### Post by scambro on 2014-02-16
> **Temüjin said:**
> Try running a non-3D desktop environment (like xfce or lxde). The ES1000 is basically a cut down version of the original Radeon with very limited 3D power. It's no surprise that Unity brings it to its knees.

Just installed LXDE and this is much more like what I was expecting an 8 core system to feel like.  I knew there were different desktop flavors but had no idea it would make this drastic of a difference...  Thanks!

---


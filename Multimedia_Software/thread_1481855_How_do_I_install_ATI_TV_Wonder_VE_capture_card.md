---
title: "How do I install ATI TV Wonder VE capture card?"
date: 2010-05-13
forum: Multimedia Software
---

### Post by Drezliok on 2010-05-13
I have a ATI TV Wonder VE capture card. It was made in 2000 so it's not new.

I can't get it to work and ultimately I am lost as to how to go about getting it to work.

It shows up in my dmesg, here is part of it

```

[   17.435143] bttv: driver version 0.9.18 loaded
[   17.435148] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.436040] bttv: Bt8xx card found (0).
[   17.436058] bttv 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.436073] bttv0: Bt878 (rev 2) at 0000:04:01.0, irq: 17, latency: 64, mmio: 0xf8fff000
[   17.436109] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[   17.436114] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[   17.436118] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.436162] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   17.436332] bttv0: tuner type=19
[   17.454053] bttv0: audio absent, no audio device found!
[   17.455356] ppdev: user-space parallel port driver
[   17.485193] All bytes are equal. It is not a TEA5767
[   17.485356] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   17.492573] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.492585] nvidia 0000:01:00.0: setting latency timer to 64
[   17.492592] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.493865] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   17.504973] tuner-simple 0-0060: creating new instance
[   17.504978] tuner-simple 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   17.505734] bttv0: registered device video0
[   17.505791] bttv0: registered device vbi0
[   17.505815] bttv0: PLL: 28636363 => 35468950 .Console: switching to colour frame buffer device 80x30
[   17.520912] . ok
[   17.649494] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.649584] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.733222] hda_codec: ALC888: BIOS auto-probing.
[   17.734669] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   17.888826] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[   18.223691] type=1505 audit(1273727329.344:6):  operation="profile_load" pid=822 name="/usr/share/gdm/guest-session/Xsession"
[   18.238164] type=1505 audit(1273727329.360:7):  operation="profile_replace" pid=824 name="/sbin/dhclient3"
[   18.238976] type=1505 audit(1273727329.360:8):  operation="profile_replace" pid=824 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.239419] type=1505 audit(1273727329.360:9):  operation="profile_replace" pid=824 name="/usr/lib/connman/scripts/dhclient-script"
[   18.245320] r8169: eth0: link up

```

But I can get any programs to use the card.

Like I said I am pretty much lost.

Thankyou for your time,
Drezliok

---


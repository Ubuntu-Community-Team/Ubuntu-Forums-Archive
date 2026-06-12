---
title: "Sabrent saa7130 Tv Tuner Help"
date: 2008-04-26
forum: Multimedia Software
---

### Post by vbman11 on 2008-04-26
I have a sabrent pci tv tuner (saa7130). I have mostly gotten it to work, but the "composite 1" and "television" inputs are switched in all the TV programs I try to use. I am now using 64bit and I had it working in 32bit but I can't remember what I did to fix the problem(When I switched to 64bit I didn't backup /etc/modprobe.d/saa7134). Also I remember when I had it "working" in 32bit, the lower channels weren't working when my TV could get them perfectly.

dmesg output:
[ 45.432932] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 45.433335] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[ 45.433345] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[ 45.433351] saa7130[0]: found at 0000:01:09.0, rev: 1, irq: 17, latency: 32, mmio: 0xfd9fe000
[ 45.433357] saa7130[0]: subsystem: 1131:0000, board: Proteus Pro 2309 [card=98,insmod option]
[ 45.433365] saa7130[0]: board init: gpio is 4000
[ 45.433417] input: saa7134 IR (Proteus Pro 2309) as /devices/pci0000:00/0000:00:04.0/0000:01:09.0/input/input6
[ 45.592082] saa7130[0]: Huh, no eeprom present (err=-5)?
[ 45.611481] saa7130[0]: i2c scan: found device @ 0xc0 [tuner (analog)]
[ 45.756422] All bytes are equal. It is not a TEA5767
[ 45.756428] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[ 45.756455] tuner-simple 2-0060: type set to 69 (Tena TNF 5335 and similar models)
[ 45.756457] tuner 2-0060: type set to Tena TNF 5335 and s
[ 45.756460] tuner-simple 2-0060: type set to 69 (Tena TNF 5335 and similar models)
[ 45.756462] tuner 2-0060: type set to Tena TNF 5335 and s
[ 45.879329] saa7130[0]: registered device video0 [v4l2]
[ 45.879364] saa7130[0]: registered device vbi0
[ 45.879908] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[ 45.879911] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [AIGP] -> GSI 22 (level, low) -> IRQ 22
[ 45.879917] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[ 45.880073] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 169.12 Thu Feb 14 17:51:09 PST 2008
[ 45.949720] saa7134 ALSA driver for DMA sound loaded
[ 45.949751] saa7130[0]/alsa: saa7130[0] at 0xfd9fe000 irq 17 registered as card -2

/etc/modprobe.d/saa7134:
options saa7134 card=98 tuner=69 i2c_scan=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa

PLEASE HELP!

---

### Post by NaOH on 2009-10-04
Same thing, anyone experience this as well, any solutions?

---

### Post by NaOH on 2009-10-04
Got it working on my system; as I said, similar symptoms, my issue was simply using the "wrong" card/tuner.  More experimentation revealed many combinations that worked.  The card described as the Sabrent TVFM yada yada was actually a poor match; for my card the Medion...7130 is what did the trick (#10 on the list of cards) and I settled on 43 for the tuner.

Point is, with these cheapies you need to try out a lot of combos.  The price you pay in toil for a low cost card.

---


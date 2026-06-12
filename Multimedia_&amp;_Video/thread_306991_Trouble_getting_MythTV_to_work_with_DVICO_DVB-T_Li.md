---
title: "Trouble getting MythTV to work with DVICO DVB-T Lite"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by Causinc on 2006-11-25
I'm confused. From what I've read this card should work, so why if it is detected correctly does it not seem to work?

Long story short, installed mythtv, assumed it would work. After reading various posts, I loaded the bt878 module the card still didn't appear in the mythtv setup list.

So after reading more posts, I tried removing the modules for bttv and bt878 and did

modprobe bttv

The following are the lines from dmesg that show that bttv is correctly identifying the card:

[17182796.228000] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[17182798.324000] bttv0: unloading
[17182814.688000] bttv: driver version 0.9.16 loaded
[17182814.688000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17182814.688000] bttv: Bt8xx card found (0).
[17182814.688000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 177
[17182814.688000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 177, latency: 64, mmio: 0xcfffe000
[17182814.688000] bttv0: detected: DViCO FusionHDTV DVB-T Lite [card=128], PCI subsystem ID is 18ac:db10
[17182814.692000] bttv0: using: DViCO FusionHDTV DVB-T Lite [card=128,autodetected]
[17182814.692000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17182814.692000] bttv0: using tuner=-1
[17182814.692000] bttv0: add subdevice "dvb0"

But note the tuner=-1 bit - that doesn't sound right. And it didn't load the bt878 module even though it identified the card correctly :(

So - unload again and l;oad the bt878 module first then the bttv module. Dmesg gives me this:

[17183605.920000] bttv: driver version 0.9.16 loaded
[17183605.920000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17183605.920000] bttv: Bt8xx card found (0).
[17183605.920000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 177
[17183605.920000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 177, latency: 64, mmio: 0xcfffe000
[17183605.920000] bttv0: detected: DViCO FusionHDTV DVB-T Lite [card=128], PCI subsystem ID is 18ac:db10
[17183605.920000] bttv0: using: DViCO FusionHDTV DVB-T Lite [card=128,autodetected]
[17183605.920000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17183605.924000] bttv0: using tuner=-1
[17183605.924000] bttv0: add subdevice "dvb0"
[17183605.956000] bt878: AUDIO driver version 0.0.0 loaded
[17183605.956000] bt878: Bt878 AUDIO function found (0).
[17183605.956000] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 177
[17183605.956000] bt878(0): Bt878 (rev 17) at 00:09.1, irq: 177, latency: 64, memory: 0xcffff000

So - no difference there - seems the bt878 module is only for the audio??

So I give up - too hard basket. Anyone like to point me in the direction of a HOWTO that spells out the steps I *should* need to take to get this to work, assuming everything else is correct?

Ta

Ron

---


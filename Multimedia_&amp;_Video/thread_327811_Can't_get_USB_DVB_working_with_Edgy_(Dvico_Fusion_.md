---
title: "Can't get USB DVB working with Edgy (Dvico Fusion Duo Card)"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by BambooClaw on 2006-12-29
I have a Dvico Fusion HDTV DVB-T Duo card and I am having trouble getting the USB part of the card working.  I also have the Dvico Fusion Lite which is working correctly.

Is there still a Firmware part that needs to compiled for the Edgy kernel?

dmesg extract:
[17179595.928000] cx2388x v4l2 driver version 0.0.5 loaded
[17179595.984000] bttv: driver version 0.9.16 loaded
[17179595.984000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179596.020000] cx2388x dvb driver version 0.0.5 loaded
[17179596.032000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179596.040000] nvidia: module license 'NVIDIA' taints kernel.
[17179596.060000] intel8x0_measure_ac97_clock: measured 54022 usecs
[17179596.060000] intel8x0: clocking to 46862
[17179596.060000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[17179596.060000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[17179596.060000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179596.060000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 209
[17179596.060000] CORE cx88[0]: subsystem: 18ac:db50, board: DViCO FusionHDTV DVB-T Dual Digital [card=44,autodetected]
[17179596.060000] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
[17179596.084000] ts: Compaq touchscreen protocol output
[17179596.276000] cx88[0]/0: found at 0000:02:09.0, rev: 5, irq: 209, latency: 32, mmio: 0xec000000
[17179596.276000] cx88[0]/0: registered device video0 [v4l2]
[17179596.276000] cx88[0]/0: registered device vbi0
[17179596.276000] bttv: Bt8xx card found (0).
[17179596.276000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179596.276000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 217
[17179596.276000] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 217, latency: 32, mmio: 0xef000000
[17179596.276000] bttv0: detected: DViCO FusionHDTV DVB-T Lite [card=128], PCI subsystem ID is 18ac:db10
[17179596.276000] bttv0: using: DViCO FusionHDTV DVB-T Lite [card=128,autodetected]
[17179596.276000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[17179596.276000] bttv0: using tuner=-1
[17179596.276000] bttv0: add subdevice "dvb0"
[17179596.276000] ACPI: PCI Interrupt 0000:02:09.2[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 209
[17179596.276000] cx88[0]/2: found at 0000:02:09.2, rev: 5, irq: 209, latency: 32, mmio: 0xed000000
[17179596.276000] cx88[0]/2: cx2388x based dvb card
[17179596.276000] DVB: registering new adapter (cx88[0]).
[17179596.276000] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[17179596.288000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[17179596.288000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 217
[17179596.288000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179596.536000] cx2388x blackbird driver version 0.0.5 loaded
[17179596.568000] bt878: AUDIO driver version 0.0.0 loaded
[17179596.568000] bt878: Bt878 AUDIO function found (0).
[17179596.568000] ACPI: PCI Interrupt 0000:02:08.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 217
[17179596.568000] bt878_probe: card id=[0xdb1018ac],[ DViCO FusionHDTV DVB-T Lite ] has DVB functions.
[17179596.568000] bt878(0): Bt878 (rev 17) at 02:08.1, irq: 217, latency: 32, memory: 0xef001000
[17179596.804000] Intel ISA PCIC probe: not found.
[17179596.860000] lp0: using parport0 (interrupt-driven).
[17179596.916000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179596.916000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179597.060000] DVB: registering new adapter (bttv0).
[17179597.068000] DVB: registering frontend 1 (Zarlink MT352 DVB-T)...
[17179597.188000] Adding 1951888k swap on /dev/disk/by-uuid/f8396b42-2c82-470f-ad70-c6cfa38f9e1a.  Priority:-1 extents:1 across:1951888k
[17179597.968000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.968000] md: bitmap version 4.39
[17179598.308000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179598.340000] NET: Registered protocol family 10
[17179598.340000] lo: Disabled Privacy Extensions
[17179598.340000] IPv6 over IPv4 tunneling driver

---


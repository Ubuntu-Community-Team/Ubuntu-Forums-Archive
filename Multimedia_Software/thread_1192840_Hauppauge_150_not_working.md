---
title: "Hauppauge 150 not working"
date: 2009-06-20
forum: Multimedia Software
---

### Post by ketom2000 on 2009-06-20
I just installed a Hauppauge 150 on a clean Jaunty system and am having difficulties getting it working.

When I try tvtime I see the following message:

No such device or address.

Cannot open capture device /dev/vide0

When check dmesg this is what I get for the capture card part:

[   11.105069] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x6000
[   11.224264] parport_pc 00:05: reported by Plug and Play ACPI
[   11.224318] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   11.613561] Linux agpgart interface v0.103
[   11.820478] Linux video capture interface: v2.00
[   11.856336] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.915620] ppdev: user-space parallel port driver
[   12.194377] nvidia: module license 'NVIDIA' taints kernel.
[   12.461556] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 18
[   12.461572] nvidia 0000:02:00.0: PCI INT A -> Link[LNEA] -> GSI 18 (level, low) -> IRQ 18
[   12.461581] nvidia 0000:02:00.0: setting latency timer to 64
[   12.463110] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.537244] ivtv:  Start initialization, version 1.4.0
[   12.537421] ivtv0: Initializing card #0
[   12.537426] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   12.538946] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 17
[   12.538962] ivtv 0000:03:07.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[   12.588537] tveeprom 1-0050: Hauppauge model 26582, rev F0B2, serial# 10460293
[   12.588540] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   12.588542] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   12.588545] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   12.588547] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   12.588549] tveeprom 1-0050: has no radio
[   12.588551] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   12.613385] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.739708] cx25840 1-0044: cx25  0-21 found @ 0x88 (ivtv i2c driver #0)
[   12.745303] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   12.748260] wm8775 1-001b: I2C: cannot write 000 to register R23
[   12.750996] wm8775 1-001b: I2C: cannot write 000 to register R7
[   12.753883] wm8775 1-001b: I2C: cannot write 021 to register R11
[   12.762330] wm8775 1-001b: I2C: cannot write 102 to register R12
[   12.765971] wm8775 1-001b: I2C: cannot write 000 to register R13
[   12.768733] wm8775 1-001b: I2C: cannot write 1d4 to register R14
[   12.772582] wm8775 1-001b: I2C: cannot write 1d4 to register R15
[   12.775447] wm8775 1-001b: I2C: cannot write 1bf to register R16
[   12.778195] wm8775 1-001b: I2C: cannot write 185 to register R17
[   12.781844] wm8775 1-001b: I2C: cannot write 0a2 to register R18
[   12.784791] wm8775 1-001b: I2C: cannot write 005 to register R19
[   12.787595] wm8775 1-001b: I2C: cannot write 07a to register R20
[   12.792156] wm8775 1-001b: I2C: cannot write 102 to register R21
[   12.792547] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   12.792622] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   12.792665] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   12.792711] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   12.792714] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   12.792748] ivtv:  End initialization
[   12.811489] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   12.811495] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   12.811596] HDA Intel 0000:00:10.1: setting latency timer to 64


If I try cat /dev/video0 > test.mpg I get an error:  No such device or address.

What do I need to get this working?

---

### Post by saedelaere on 2009-07-09
First of all tvtime will never work with this device. You could try [TV-Viewer]("http://home.arcor.de/saedelaere/index_eng.html"). Be sure to use the latest version.

But it seems your card isn't initialized correct. 
What do you get when you execute

```
ls /dev/video*
```
?

---


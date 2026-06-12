---
title: "Problem with tv card Asus P7131"
date: 2008-05-02
forum: Multimedia Software
---

### Post by pentel on 2008-05-02
Hi guys!
I wanna congrats all people involved in Ubuntu project because its a excellent operating system!
But now i have a little problem with my tvcard.
I have a Asus My Cinema P7131 (Not the hybrid one) and i installed tvtime to see tv but in the first time i didn't have sound.
With some search i found a command to put in the terminal

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -D surround41

With that line i have sound but i have a little out of sync(+-100ms)
Any one have a idea?:)

Thanks in advance!

ps: My sound card is sound blaster Live!
ps2: Sorry my bad English 

Ps3: Ubuntu ROCKS!:guitar:

---

### Post by a_kiil42 on 2008-09-05
I have the same problem P7131, picture but no sound
my sounddevice is the ac97 onboard sound

[PHP][   54.013398] Linux video capture interface: v2.00
[   54.325082] saa7130/34: v4l2 driver version 0.2.14 loaded
[   54.325185] ACPI: PCI Interrupt 0000:04:07.0[A] -> GSI 22 (level, low) -> IRQ 22
[   54.325192] saa7133[0]: found at 0000:04:07.0, rev: 209, irq: 22, latency: 32, mmio: 0xfeaff000
[   54.325197] saa7133[0]: subsystem: 1043:4845, board: ASUS TV-FM 7135 [card=53,autodetected]
[   54.325205] saa7133[0]: board init: gpio is 40000
[   54.460963] saa7133[0]: i2c eeprom 00: 43 10 45 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   54.460970] saa7133[0]: i2c eeprom 10: 00 ff e2 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   54.460974] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 88 ff ff ff ff
[   54.460979] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.460983] saa7133[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
[   54.460987] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.460991] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.460995] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.736650] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   54.784597] tda8290 1-004b: setting tuner address to 61
[   54.888518] tuner 1-004b: type set to tda8290+75a
[   54.936453] tda8290 1-004b: setting tuner address to 61
[   54.965599] nvidia: module license 'NVIDIA' taints kernel.
[   55.040350] tuner 1-004b: type set to tda8290+75a
[   55.299908] logips2pp: Detected unknown logitech mouse model 20
[   55.326560] saa7133[0]: registered device video0 [v4l2]
[   55.326577] saa7133[0]: registered device vbi0
[   55.326590] saa7133[0]: registered device radio0
[   55.326797] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[   55.413184] saa7134 ALSA driver for DMA sound loaded
[   55.413208] saa7133[0]/alsa: saa7133[0] at 0xfeaff000 irq 22 registered as card -2
[   55.768835] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   55.798331] parport_pc 00:06: reported by Plug and Play ACPI
[   55.798448] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   56.351055] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET 
[   56.351623] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 1 access is not valid [0xffffffff], removing mixer. 
[   56.351630][ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/intel8x0.c:2155: Unable to initialize codec #1
[   56.407014] intel8x0_measure_ac97_clock: measured 54996 usecs
[   56.407018] intel8x0: clocking to 48000
[   56.407664] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   56.407818] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   58.984625] lp0: using parport0 (interrupt-driven).
[   59.065402] Adding 3012148k swap on /dev/sda5.  Priority:-1 extents:1 across:[/PHP]

I can see there is a problem, but I don't know how to fix it. Can anyone help with a solution.

---

### Post by xfire on 2008-09-05
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---


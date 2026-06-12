---
title: "Getting DVB-T to work"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by reesje on 2008-01-05
Hi guys

I am having a bit of a problem with my DVB-T PCMCIA card (MSI TV @nywhere A/D NB). The TV card is detected as UNKNOWN/GENERIC out of the box, but by adding the following code to```
options saa7134 card=94
``` to /etc/modprobe.d/options it seems to setup the card right, actually an orange led lights up on the PCMCIA card, which should indicate that the card is working. But Kaffeine does not recognize that there in fact is a DVB-T card in the PC. So I looked at the output of dmesg, and I see the following:
```
....
[   18.800000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   19.492000] intel8x0_measure_ac97_clock: measured 55506 usecs
[   19.492000] intel8x0: clocking to 48000
[   19.492000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[   19.492000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   19.492000] saa7133[0]: found at 0000:04:00.0, rev: 208, irq: 17, latency: 0, mmio: 0x8c000000
[   19.492000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   19.492000] saa7133[0]: subsystem: 4e42:3502, board: LifeView FlyDVB-T Hybrid Cardbus [card=94,insmod option]
[   19.492000] saa7133[0]: board init: gpio is 8210000
[   19.628000] saa7133[0]: i2c eeprom 00: 42 4e 02 35 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   19.628000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[   19.628000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 eb ff ff ff ff
[   19.628000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.628000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 32 15 ff ff ff ff
[   19.628000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.628000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.628000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.740000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   19.788000] tuner 0-004b: setting tuner address to 61
[   19.828000] tuner 0-004b: type set to tda8290+75a
[   21.196000] tuner 0-004b: setting tuner address to 61
[   21.236000] tuner 0-004b: type set to tda8290+75a
[   22.556000] saa7133[0]: registered device video0 [v4l2]
[   22.556000] saa7133[0]: registered device vbi0
[   22.556000] saa7133[0]: registered device radio0
[   22.656000] saa7134 ALSA driver for DMA sound loaded
[   22.656000] saa7133[0]/alsa: saa7133[0] at 0x8c000000 irq 17 registered as card -2
[   22.736000] DVB: registering new adapter (saa7133[0]).
[   22.736000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   22.808000] tda1004x: setting up plls for 48MHz sampling clock
[   23.076000] lp: driver loaded but no devices found
[   24.808000] tda1004x: found firmware revision 29 -- ok
[   25.236000] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[   25.612000] EXT3 FS on sda1, internal journal
[   29.252000] input: Lid Switch as /class/input/input6
[   29.252000] ACPI: Lid Switch [LID]
[   29.284000] input: Power Button (CM) as /class/input/input7
[   29.288000] ACPI: Power Button (CM) [PBTN]
[   29.320000] input: Sleep Button (CM) as /class/input/input8
[   29.324000] ACPI: Sleep Button (CM) [SBTN]
[   29.632000] ACPI: Battery Slot [BAT0] (battery present)
[   29.632000] ACPI: Battery Slot [BAT1] (battery absent)
[   29.644000] ACPI: ACPI Dock Station Driver 
[   29.672000] ACPI: AC Adapter [AC] (on-line)
[   29.700000] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: found ejectable bay
[   29.700000] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: Adding notify handler
[   29.700000] ACPI: Error installing bay notify handler
[   29.700000] ACPI: Bay [\_SB_.PCI0.IDE0.SEC0.MAST] Added
[   29.716000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   31.468000] ppdev: user-space parallel port driver
[   31.796000] audit(1199551306.565:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4911 profile="/usr/sbin/cupsd"
[   31.860000] apm: BIOS not found.
[   32.212000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   32.320000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   32.340000] NFSD: starting 90-second grace period
[   34.964000] Failure registering capabilities with primary security module.
[   35.068000] tda1004x: setting up plls for 48MHz sampling clock
[   35.216000] Bluetooth: L2CAP ver 2.8
[   35.216000] Bluetooth: L2CAP socket layer initialized
[   35.348000] Bluetooth: RFCOMM socket layer initialized
[   35.348000] Bluetooth: RFCOMM TTY layer initialized
[   35.348000] Bluetooth: RFCOMM ver 1.8
[   37.020000] tda1004x: found firmware revision 29 -- ok
[   72.108000] tda827xa_set_params: could not write to tuner at addr: 0xc2
[   72.984000] tda827xa_set_params: could not write to tuner at addr: 0xc2
......

```
The first part looks quite allright, but I believe my problem lies in the error message in the last two lines (it just continues like that for many more lines).

For your information I have another PC with a ASUSTeK P7131 Hybrid PCI card and on that I have no problems running DVB-T programs with Kaffeine and it is using the same chip, and I have installed the same packages.

Can anybody help me?

Thanks very very much in advance!

BR,
René

---

### Post by reesje on 2008-01-06
Following this guide:
[http://www.linuxtv.org/v4lwiki/index.php/MSI_TV@nywhere_A/D_NB](http://www.linuxtv.org/v4lwiki/index.php/MSI_TV@nywhere_A/D_NB)
And the card works!

BR,
René

---


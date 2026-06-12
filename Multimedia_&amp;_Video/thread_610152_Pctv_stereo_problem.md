---
title: "Pctv stereo problem"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by codename_nixon on 2007-11-11
Hello all
            guys i hv a pctvstereo tv tuner card [100]i
i fail to get it working  ihv read many thrads on this forum butbeing a complet linux\ubuntu noob i dont get a thing 

the only thing i could understand ws i have to chk for  dmesg

here is it output
```
[   43.024939] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   43.035187] heci: Intel(R) AMT Management Interface - version 3.1.0.31
[   43.035189] heci: Copyright (c) 2003 - 2007 Intel Corporation.
[   43.070600] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:96:18:d6
[   43.101921] Linux agpgart interface v0.102 (c) Dave Jones
[   43.143790] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   43.143843] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 22
[   43.143849] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   43.144162] heci: link layer has been established.
[   43.150499] Linux video capture interface: v2.00
[   43.217761] saa7130/34: v4l2 driver version 0.2.14 loaded
[   43.245926] heci: heci driver initialization successful.
[   43.245951] agpgart: Detected an Intel G33 Chipset.
[   43.247532] agpgart: Detected 7164K stolen memory.
[   43.261138] agpgart: AGP aperture is 256M @ 0xc0000000
[   43.261549] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 21 (level, low) -> IRQ 20
[   43.261558] saa7134[0]: found at 0000:06:00.0, rev: 1, irq: 20, latency: 32, mmio: 0xd0004800
[   43.261564] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[   43.261577] saa7134[0]: board init: gpio is 0
[   43.320389] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   43.320404] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   43.393449] saa7134[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   43.393460] saa7134[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   43.393469] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[   43.393478] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.393487] saa7134[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 03 ff ff ff ff ff ff ff ff
[   43.393496] saa7134[0]: i2c eeprom 50: 0c 22 17 36 03 0b bc 5a ff ff ff ff ff ff ff ff
[   43.393505] saa7134[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[   43.393513] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.465336] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   43.465357] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   43.481310] tuner 0-0060: Chip ID is not zero. It is not a TEA5767
[   43.481313] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   43.497305] tuner 0-0060: microtune: companycode=3cbf part=42 rev=2f
[   43.525223] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   43.529236] tuner 0-0060: microtune MT2050 found, OK
[   43.545230] tuner 0-0060: microtune: companycode=3cbf part=42 rev=2f
[   43.577161] tuner 0-0060: microtune MT2050 found, OK
[   43.579789] saa7134[0]: registered device video0 [v4l2]
[   43.579811] saa7134[0]: registered device vbi0
[   43.593954] saa7134 ALSA driver for DMA sound loaded
[   43.593976] saa7134[0]/alsa: saa7134[0] at 0xd0004800 irq 20 registered as card -2
[   44.037010] lp: driver loaded but no devices found
[   44.081156] Adding 2168732k swap on /dev/sda11.  Priority:-1 extents:1 across:2168732k
[   44.371519] EXT3 FS on sda10, internal journal
[   44.919099] No dock devices found.
[   45.057620] input: Power Button (FF) as /class/input/input4
[   45.057727] ACPI: Power Button (FF) [PWRF]
[   45.058305] input: Sleep Button (CM) as /class/input/input5
[   45.058408] ACPI: Sleep Button (CM) [SLPB]
[   45.711677] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   45.711681] apm: disabled - APM is not SMP safe.
[   45.852917] Failure registering capabilities with primary security module.
[   46.361843] cdrom: This disc doesn't have any tracks I recognize!
[   47.511424] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   47.511429] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
[   48.307742] [drm] Initialized drm 1.1.0 20060810
[   48.314962] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ

```

guys my country is India  and plz hlp me installing n viewing tv on my pc

plz b as elaborative and as detailed as possible [ totally linux noob]......recently started using ubuntu cuse got frustrated of MS]

thx

---

### Post by rsramkee on 2007-11-30
you have a pinnacle card that uses the saa7134 chipset. 

One way to get this working is to modify some driver options by doing the following:

'sudo gedit /etc/modprobe.d/options'

this will opena the filefor editing. here you need to enter the following line:
option saa7134 card=x tuner=y.

Now, the values of x and y are critical. you can find the correct values, based on your card type, from [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

After entering these values in this file, reboot your system. Your card should be recognized.

run 'tvtime-scanner' and see if it is able to do an auto scan. If that works, tvtime should see all your channels.

---


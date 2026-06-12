---
title: "TV tuner not working so well in 8.10"
date: 2008-11-10
forum: Multimedia Software
---

### Post by gh81 on 2008-11-10
Hi,

A couple of days ago I upgraded from Hardy to Intrepid, and I have found some problems with my TV tuner card, which was working perfectly in Hardy.

The card is a Compro T300. I now find that, on loading Mythtv or any other TV viewing program, I just get static. However, if I unload the TV card kernel module (saa7134 in this case) then reload it, it all works again. After some time staring at the dmesg output, I think that when the module loads at boot time, it is unable to determine the tuner type for some reason. When I reload it, it correctly finds that the tuner number is 67.

Relevant looking parts of the dmesg output:
First, the output before reloading the drivers.

```

[   14.529653] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.530114] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   14.530124] saa7134 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   14.530130] saa7134[0]: found at 0000:01:05.0, rev: 1, irq: 16, latency: 84, mmio: 0xfd7ff000
[   14.530135] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,autodetected]
[   14.530143] saa7134[0]: board init: gpio is 841200
[   14.530207] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:04.0/0000:01:05.0/input/input7
[   14.577394] end_request: I/O error, dev sr0, sector 16298752
[   14.577400] Buffer I/O error on device sr0, logical block 4074688
[   14.589791] usbcore: registered new interface driver snd-usb-audio
[   14.607749] end_request: I/O error, dev sr0, sector 16298756
[   14.607755] Buffer I/O error on device sr0, logical block 4074689
[   14.640516] end_request: I/O error, dev sr0, sector 16298752
[   14.640522] Buffer I/O error on device sr0, logical block 4074688
[   14.640526] Buffer I/O error on device sr0, logical block 4074689
[   14.744132] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.744139] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   14.744145] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   14.744151] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744156] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   14.744161] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   14.744167] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744172] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744177] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744183] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744188] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744193] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744199] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744204] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744209] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.744214] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.756033] saa7134[0]: i2c scan: found device @ 0x10  [???]
[   14.772086] saa7134[0]: i2c scan: found device @ 0x86  [tda9887]
[   14.784189] saa7134[0]: i2c scan: found device @ 0xa0  [eeprom]
[   14.796029] saa7134[0]: i2c scan: found device @ 0xd0  [???]
[   15.000573] tuner' 2-0043: chip found @ 0x86 (saa7134[0])
[   15.035857] tda9887 2-0043: creating new instance
[   15.035860] tda9887 2-0043: tda988[5/6/7] found
[   15.052563] tuner' 2-0068: chip found @ 0xd0 (saa7134[0])
[   15.076034] tuner' 2-0068: tuner type not set
[   15.076040] tuner' 2-0068: tuner type not set
[   15.076823] saa7134[0]: registered device video0 [v4l2]
[   15.077297] saa7134[0]: registered device vbi0
[   15.148217] saa7134 ALSA driver for DMA sound loaded
[   15.148254] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 16 registered as card -2
[   15.264530] DVB: registering new adapter (saa7134[0])
[   15.264535] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...

```

And then a while later,

```

[   36.476122] tuner' 2-0068: tuner type not set
[   36.486927] tuner' 2-0068: tuner type not set
[   36.486952] tuner' 2-0068: tuner type not set
[   36.489363] tuner' 2-0068: tuner type not set
[   36.489391] tuner' 2-0068: tuner type not set
[   36.500535] tuner' 2-0068: tuner type not set

```


After I reload the drivers, I get almost the same output so I won't repeat it all. The differences are, I don't get these "tuner type not set" lines, and after the i2c stuff I get

```

[ 2431.856023] saa7134[0]: i2c scan: found device @ 0xd0  [???]
[ 2432.012027] tuner-simple 2-0061: creating new instance
[ 2432.012043] tuner-simple 2-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[ 2432.056390] saa7134[0]: registered device video0 [v4l2]
[ 2432.056471] saa7134[0]: registered device vbi0
[ 2432.097785] saa7134 ALSA driver for DMA sound loaded
[ 2432.098366] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 16 registered as card -2
[ 2432.177257] DVB: registering new adapter (saa7134[0])
[ 2432.177280] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[ 2432.236707] tda1004x: setting up plls for 48MHz sampling clock
[ 2432.236872] tuner-simple 2-0061: i2c i/o error: rc == -5 (should be 4)
[ 2432.762719] tda1004x: found firmware revision 23 -- ok

```

You can see it finds the tuner type is 67.

I've tried specifying tuner=67 for this module by creating a file in /etc/modprobe.d but it makes no difference whatsoever.

Anybody have any ideas?

---

### Post by gh81 on 2008-11-10
I forgot to mention - it's probably unrelated but just in case... I also find that now the cpu usage of mythbackend is almost 100% of 1 cpu any time it's recording. It used to be 5-10%... Just in case it has any bearing.

---

### Post by gh81 on 2008-11-11
Bump...

It may be a kernel issue. If I boot to kernel 2.6.24, the driver loads properly as before. I still have the mythtv 100% cpu usage issue though, so that's probably unrelated.

---


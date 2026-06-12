---
title: "&quot;Funny&quot; error with DVB-T Card"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by TheInfinity on 2007-12-05
Hello

my girlfriend has an IBM R60 and got a PCMCIA card "Fly-DVB-T Duo" from LifeView now - a CardBus card. She has kubuntu 7.10 with all updates. lspci says:
```
16:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
```

After installation of firmware dmesg says:
```
[ 1595.804000] pccard: CardBus card inserted into slot 0
[ 1596.204000] Linux video capture interface: v2.00
[ 1596.300000] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 1596.300000] PCI: Enabling device 0000:16:00.0 (0000 -> 0002)
[ 1596.300000] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 1596.300000] saa7133[0]: found at 0000:16:00.0, rev: 240, irq: 16, latency: 0, mmio: 0xc4000000
[ 1596.300000] PCI: Setting latency timer of device 0000:16:00.0 to 64
[ 1596.300000] saa7133[0]: subsystem: 5168:0502, board: LifeView/Typhoon/Genius FlyDVB-T Duo Cardbus [card=60,autodetected]
[ 1596.300000] saa7133[0]: board init: gpio is e010000
[ 1596.436000] saa7133[0]: i2c eeprom 00: 68 51 02 05 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 1596.436000] saa7133[0]: i2c eeprom 10: 00 ff 22 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[ 1596.436000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 aa ff ff ff ff
[ 1596.436000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1596.436000] saa7133[0]: i2c eeprom 40: ff 1c 00 c0 ff 10 ff ff c2 96 00 16 22 15 ff ff
[ 1596.436000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1596.436000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1596.436000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1596.520000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[ 1596.568000] tuner 0-004b: setting tuner address to 61
[ 1596.608000] tuner 0-004b: type set to tda8290+75
[ 1598.252000] tuner 0-004b: setting tuner address to 61
[ 1598.292000] tuner 0-004b: type set to tda8290+75
[ 1599.888000] saa7133[0]: registered device video0 [v4l2]
[ 1599.888000] saa7133[0]: registered device vbi0
[ 1599.888000] saa7133[0]: registered device radio0
[ 1599.980000] saa7134 ALSA driver for DMA sound loaded
[ 1599.984000] saa7133[0]/alsa: saa7133[0] at 0xc4000000 irq 16 registered as card -2
[ 1600.036000] DVB: registering new adapter (saa7133[0]).
[ 1600.040000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[ 1600.124000] tda1004x: setting up plls for 48MHz sampling clock
[ 1602.376000] tda1004x: timeout waiting for DSP ready
[ 1602.416000] tda1004x: found firmware revision 0 -- invalid
[ 1602.416000] tda1004x: trying to boot from eeprom
[ 1604.744000] tda1004x: timeout waiting for DSP ready
[ 1604.784000] tda1004x: found firmware revision 0 -- invalid
[ 1604.784000] tda1004x: waiting for firmware upload...
[ 1617.284000] tda1004x: found firmware revision 20 -- ok

```

Sounds well so far. But ...
- kaffeine founds broudcast stations, but crashes, if i want to see anything
- MythTV does not find anything, also a local MythTV team didnt got it
- console apps also dont find anything
- while launching kubuntu you have to switch manually via alt strg F7 to XOrg when card is plugged in, otherwise it stays in tty

I dont know any point where I can start debugging this. The local MythTV team sayd that they had the same error some days ago with a *ubuntu user, he switched to suse because he didnt found the error. I want to stay at kubuntu - but how can I get this damn DVB-T card to run?

Thanks for any help ...

---

### Post by mtron on 2007-12-05
```
[ 1602.376000] tda1004x: timeout waiting for DSP ready
[ 1602.416000] tda1004x: found firmware revision 0 -- invalid
```

this sounds to me as a firmware issue. What fw file did you try percisely?  and have you tried installing up to date dvb drivers? [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

a quote from the [wiki page]("http://www.linuxtv.org/wiki/index.php/Philips_TDA10046") on your Demodulator

> Requires a [firmware]("http://www.linuxtv.org/wiki/index.php/Firmware") to work. You need to run a script that comes with the kernel source (it downloads the windows driver and peels out the code). Then, each time the machine is booted, the firmware is loaded into the card to make it work.

---


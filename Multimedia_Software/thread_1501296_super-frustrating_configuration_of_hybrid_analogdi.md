---
title: "super-frustrating configuration of hybrid analog/digital tuner card"
date: 2010-06-04
forum: Multimedia Software
---

### Post by stilbo on 2010-06-04
Hi there
 
Please help
 
I'm fairly new to ubuntu and I want to free myselv and my family from the terrible windows grip...
 
Anyway I'm setting up a mythbuntu in the livingroom and the box "Amitech homecenter living 510". It came with a windows installation that worked (also live tv) but I became irritated by the constant windows-lacking. So I set up mythbuntu.
 
Everything works except the darn "AVerMedia MiniPCI DVB-T Hybrid M103" digital/analog tuner and I am not getting any signal. I have only analog signal anyway from the antenna.
 
when mythbackend starts up it says the following:
....
2010-06-04 10:12:51.607 Connected to database 'mythconverg' at host: localhost
2010-06-04 10:12:51.611 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(1): Failed to initialize multiplex options
2010-06-04 10:12:51.626 New DB scheduler connection
2010-06-04 10:12:51.627 Connected to database 'mythconverg' at host: localhost
2010-06-04 10:12:51.639 MediaServer::HttpServer Create Error
2010-06-04 10:12:54.630 Reschedule requested for id -1.
2010-06-04 10:12:54.769 Scheduled 0 items in 0.1 = 0.00 match + 0.13 place
2010-06-04 10:12:54.774 Seem to be woken up by USER
...

> lspci |grep Multimedia :
04:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
 
> dmesg | grep saa71*
[   18.876827] saa7130/34: v4l2 driver version 0.2.15 loaded
[   18.876897] saa7134 0000:04:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.876907] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 18, latency: 32, mmio: 0xd0200000
[   18.876916] saa7133[0]: subsystem: 1461:f636, board: AVerMedia MiniPCI DVB-T Hybrid M103 [card=145,insmod option]
[   18.876939] saa7133[0]: board init: gpio is 360000
[   18.894518] IRQ 18/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   19.050259] saa7133[0]: i2c eeprom 00: 61 14 36 f6 00 00 00 00 00 00 00 00 00 00 00 00
[   19.050273] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   19.050286] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 0e ff ff ff ff
[   19.050299] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050312] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   19.050325] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050337] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050350] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050362] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050375] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050388] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050400] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050413] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050426] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050438] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.050451] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.088119] tuner 4-0061: chip found @ 0xc2 (saa7133[0])
[   19.120565] saa7134 0000:04:01.0: firmware: requesting xc3028-v27.fw
[   29.128322] saa7133[0]: dsp access error
[   29.128326] saa7133[0]: dsp access error
[   29.156184] saa7133[0]: registered device video0 [v4l2]
[   29.156266] saa7133[0]: registered device vbi0
[   29.163213] saa7134 ALSA driver for DMA sound loaded
[   29.163231] IRQ 18/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   29.163259] saa7133[0]/alsa: saa7133[0] at 0xd0200000 irq 18 registered as card -2
[   29.733148] DVB: registering new adapter (saa7133[0])
 
 
I found the tuner firmware (xc3028-v27.fw) somewhere on the internet and placed in in firmware folder.

I have created a saa7134.conf file and it looks like this and tried to figure out the numbers by using [http://linux.sourcearchive.com/documentation/2.6.27-9.18/saa7134-cards_8c-source.html](http://linux.sourcearchive.com/documentation/2.6.27-9.18/saa7134-cards_8c-source.html):
options saa7134 card=145 tuner=71

I read that I need to configure the DVB-T card i mythtv first and then find the analog option button and configure that from there, but I cannot find it. However the card does not work in VLC or tvtime anyway
 
At this point I dont know what to do, can anyone help?

---


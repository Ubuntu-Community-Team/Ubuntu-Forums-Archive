---
title: "saa7133 - xc2028 64bit version"
date: 2010-04-21
forum: Multimedia Software
---

### Post by genux05 on 2010-04-21
Hi all, 

I am trying to get my DVB TV laptop card trying to work, I have used the extract_xc3028.pl script..

my hardware is 

Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
 
and I am running a 64bit version of kubuntu 10.4.

But I am guessing that because I am using the 64bit version and the extract_xc32028 appears to only pull out a 32bit version ? because in the errors below there appears to be a "(should be 64)" (64bit ? )

```

  52.370088] xc2028 0-0061: Loading firmware for type=MTS (4), id 0000000100000007.
[   53.370337] saa7133[0]: dsp access error
[   53.370343] saa7133[0]: dsp access error
[   53.370354] saa7133[0]: dsp access error
[   53.370357] saa7133[0]: dsp access error
[   53.410211] saa7133[0]: registered device video1 [v4l2]
[   53.410247] saa7133[0]: registered device vbi0
[   53.420520] saa7134 ALSA driver for DMA sound loaded
[   53.420538] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   53.420567] saa7133[0]/alsa: saa7133[0] at 0xd2005000 irq 16 registered as card -2
[   53.446547] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.446702] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.446704] xc2028 0-0061: -5 returned from send
[   53.446708] xc2028 0-0061: Error -22 while loading base firmware
[   53.502577] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.502771] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.502773] xc2028 0-0061: -5 returned from send
[   53.502776] xc2028 0-0061: Error -22 while loading base firmware
[   53.503096] xc2028 0-0061: Error on line 1137: -5
[   53.503224] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.503414] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.503416] xc2028 0-0061: -5 returned from send
[   53.503418] xc2028 0-0061: Error -22 while loading base firmware
[   53.562545] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.562741] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.562743] xc2028 0-0061: -5 returned from send
[   53.562747] xc2028 0-0061: Error -22 while loading base firmware
[   53.563062] xc2028 0-0061: Error on line 1137: -5
[   53.563501] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.563692] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.563694] xc2028 0-0061: -5 returned from send
[   53.563697] xc2028 0-0061: Error -22 while loading base firmware
[   53.623139] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.623333] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.623336] xc2028 0-0061: -5 returned from send
[   53.623340] xc2028 0-0061: Error -22 while loading base firmware
[   53.623526] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.623717] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.623719] xc2028 0-0061: -5 returned from send
[   53.623721] xc2028 0-0061: Error -22 while loading base firmware
[   53.682593] xc2028 0-0061: Loading firmware for type=BASE F8MHZ MTS (7), id 0000000000000000.
[   53.682789] xc2028 0-0061: i2c output error: rc = -5 (should be 64)
[   53.682792] xc2028 0-0061: -5 returned from send
[   53.682795] xc2028 0-0061: Error -22 while loading base firmware
[   53.683227] xc2028 0-0061: Error on line 1137: -5

```

this is how I got the HDTV drivers

```

# In order to use, you need to:
#       1) Download the windows driver with something like:
#               wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
#       2) Extract the file hcw85bda.sys from the zip into the current dir:
#               unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
#       3) run the script:
#               ./extract_xc3028.pl
#       4) copy the generated file:
#               cp xc3028-v27.fw /lib/firmware

```

any advice ?

---

### Post by dvjunk on 2012-01-03
Not directly related, but wanted to post my findings on saa7133 and 64-bit Ubuntu.
I did a recent install of Mythbuntu 11.10 64-bit and had problems getting my Kworld ATSC110 tuner card working. I wasn't sure if it would work under 64-bit, but it did.
I followed the instructions at:
[http://linuxtv.org/wiki/index.php/KWorld_ATSC_110](http://linuxtv.org/wiki/index.php/KWorld_ATSC_110)
I get a dsp access error from dmesg (see below) but it still works.

The firmware seems to be loading OK from the 
dmesg | grep nxt
output below

dmesg | grep saa7
[    5.613498] saa7130/34: v4l2 driver version 0.2.16 loaded
[    5.613598] saa7134 0000:02:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.613604] saa7133[0]: found at 0000:02:05.0, rev: 240, irq: 20, latency: 64, mmio: 0xfe8ff800
[    5.613610] saa7133[0]: subsystem: 17de:7350, board: Kworld ATSC110/115 [card=90,autodetected]
[    5.613628] saa7133[0]: board init: gpio is 100
[    5.768026] saa7133[0]: i2c eeprom 00: de 17 50 73 ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768032] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768038] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768043] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768048] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768053] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768058] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768063] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768068] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768073] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768078] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768083] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768088] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768093] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768098] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    5.768103] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.052236] saa7133[0]: dsp access error
[    6.052357] saa7133[0]: registered device video0 [v4l2]
[    6.052378] saa7133[0]: registered device vbi0
[    6.081932] saa7134 ALSA driver for DMA sound loaded
[    6.081952] saa7133[0]/alsa: saa7133[0] at 0xfe8ff800 irq 20 registered as card -2
[    6.200030] DVB: registering new adapter (saa7133[0])


dmesg | grep nxt
[    6.192017] nxt200x: NXT2004 Detected
[    6.212032] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[    6.401509] nxt2004: Waiting for firmware upload(2)...
[    7.948034] nxt2004: Firmware upload complete

---


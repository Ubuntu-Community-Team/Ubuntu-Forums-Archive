---
title: "Avertv dvb-s hybrid+fm not working under mythbuntu"
date: 2008-05-08
forum: Mythbuntu
---

### Post by bvidinli on 2008-05-08
i use mythbuntu 8.04,

i have Avertv dvb-s hybrid+fm,

i cannot watch tv with mythbuntu.
scan cannot find any channel
i test it with tvtime-scanner --norm=PAL
no result, tvtime cannot find any channel


root@bvidinli-desktop:/etc/tvtime# tvtime-scanner --norm=PAL --input=2
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
station: Adding frequency table Custom, all channels active
videoinput: Using video4linux2 driver 'saa7134', card ':Zolid Xpert TV7134' (bus PCI:0000:00:14.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Maximum input width: 720 pixels.
Scanning from  44,00 MHz to 958,00 MHz.


root@bvidinli-desktop:/etc/tvtime# uname -a
Linux bvidinli-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
root@bvidinli-desktop:/etc/tvtime#


here is dmesg out.

[35406.750724] saa7130/34: v4l2 driver version 0.2.14 loaded
[35406.752101] saa7133[0]: found at 0000:00:14.0, rev: 209, irq: 5, latency: 32, mmio: 0xde003000
[35406.752126] saa7133[0]: subsystem: 1461:a7a2, board: :Zolid Xpert TV7134 [card=43,insmod option]
[35406.752152] saa7133[0]: board init: gpio is 2f600
[35406.891253] saa7133[0]: i2c eeprom 00: 61 14 a2 a7 ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891285] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891308] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891331] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891354] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891377] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891400] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[35406.891423] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[53075.881927] saa7133[0]: registered device video0 [v4l2]
[53075.882015] saa7133[0]: registered device vbi0
[35407.132143] saa7134 ALSA driver for DMA sound loaded
[35407.133342] saa7133[0]/alsa: saa7133[0] at 0xde003000 irq 5 registered as card -2

---


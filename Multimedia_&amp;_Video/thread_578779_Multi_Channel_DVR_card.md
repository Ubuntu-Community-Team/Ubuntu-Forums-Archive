---
title: "Multi Channel DVR card"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by riscsys on 2007-10-17
hELLO
I have a 8 chip 8 channel real time saa7130 dvr card.I am using zoneminder digital servelance system on my pc.
I can record 8 channel camera videos.

But 
When I need more channel cameras and I get a one the same card.
My first 8 channel and other card one channel working but not working other 7 channel .

dmesg 
[   15.021467] saa7130[9]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   15.021476] saa7130[9]: board init: gpio is 10000
[   15.126560] saa7130[9]: Huh, no eeprom present (err=-5)?
[   15.126585] saa7130[9]: can't register video device
[   15.126632] saa7134: probe of 0000:07:0f.0 failed with error -23
[   15.412335] saa7134 ALSA driver for DMA sound loaded
[   15.412362] saa7130[0]/alsa: saa7130[0] at 0xff8ffc00 irq 19 registered as card -2
[   15.412454] saa7130[1]/alsa: saa7130[1] at 0xff8ff800 irq 20 registered as card -1
[   15.412536] saa7130[2]/alsa: saa7130[2] at 0xff8ff400 irq 21 registered as card -1
[   15.412611] saa7130[3]/alsa: saa7130[3] at 0xff8ff000 irq 22 registered as card -1
[   15.412686] saa7130[4]/alsa: saa7130[4] at 0xff8fec00 irq 19 registered as card -1
[   15.412764] saa7130[5]/alsa: saa7130[5] at 0xff8fe800 irq 20 registered as card -1
[   15.412840] saa7130[6]/alsa: saa7130[6] at 0xff8fe400 irq 21 registered as card -1
[   15.412917] saa7130[7]/alsa: saa7130[7] at 0xff8fe000 irq 22 registered as card -1
[   15.412995] saa7130[8]/alsa: saa7130[8] at 0xff9ffc00 irq 20 registered as card -1
[IMG]http://www.ilkerilgen.com/weblog/wp-content/uploads/2007/hardwareinfor.jpg[/IMG]

Thank you
Ops My system
Asus p5b mainboard
intel core2duo  cpu
2048 Ram
ati adeon x1050 VGA 
320 Gb sata disk and DWDRW

---


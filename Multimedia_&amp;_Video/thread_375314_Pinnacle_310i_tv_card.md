---
title: "Pinnacle 310i tv card"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by MadeR on 2007-03-03
Adding "options saa7134 card=77 tuner=54" in /etc/modprobe.d/options, I successed having my tv card shown by dmesg.

[17179590.784000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179590.796000] saa7133[0]: found at 0000:02:0a.0, rev: 209, irq: 217, latency: 32, mmio: 0xf1026000
[17179590.796000] saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 40i/50i/110i (saa7133) [card=77,insmod option]
[17179590.796000] saa7133[0]: board init: gpio is 600e000
[17179590.908000] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[17179590.948000] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179590.948000] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2e 39 35 ff ff
[17179590.948000] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e7 ff 21 00 c2
[17179590.948000] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff 15 0e 6c a3 eb 03 c7 81 35
[17179590.948000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179590.948000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179590.948000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179590.948000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.056000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[17179591.216000] saa7133[0]: registered device video0 [v4l2]
[17179591.216000] saa7133[0]: registered device vbi0
[17179591.216000] saa7133[0]: registered device radio0
[17179591.232000] saa7134 ALSA driver for DMA sound loaded
[17179591.232000] saa7133[0]/alsa: saa7133[0] at 0xf1026000 irq 217 registered as card -1


Now the problem is that no /dev/dvb device appear: is it normal?
What program can I use to listen to radio?
What program can I use to watch DVB-T broadcasting? maybe mythtv?
Is there a better program than alevt for teletext?

---

### Post by david_2001 on 2007-03-03
[LIST]
[*]For the first question, take a look at [http://linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i](http://linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_310i)
[*]For the third question, I would try kaffeine first.  MythTV is hard work to install and get running.
[*]For the fourth, not really.  Kdetv has a teletext viewer but I don't find kdetv as a whole to be very stable.  XdTV - try it, it's cute and can record TV, though it's not in the Ubuntu repositories - uses AleVT.
[/LIST]

---

### Post by MadeR on 2007-03-03
:mad: :roll:  
does anybody know whether is there or not a stable branch for this dvb/v4l project? (I'm starting to miss FreeBSD STABLE(tested and functioning before commitment)/UNSTABLE way of doing things)

mader@silmarillion:~/v4l-dvb$ make
make -C /home/mader/v4l-dvb/v4l
make[1]: Entering directory `/home/mader/v4l-dvb/v4l'
creating symbolic links...
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/mader/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/mader/v4l-dvb/v4l/ivtv-driver.o
/home/mader/v4l-dvb/v4l/ivtv-driver.c: In function 'ivtv_probe':
/home/mader/v4l-dvb/v4l/ivtv-driver.c:1170: error: 'IRQF_SHARED' undeclared (first use in this function)
/home/mader/v4l-dvb/v4l/ivtv-driver.c:1170: error: (Each undeclared identifier is reported only once
/home/mader/v4l-dvb/v4l/ivtv-driver.c:1170: error: for each function it appears in.)
/home/mader/v4l-dvb/v4l/ivtv-driver.c:1170: error: 'IRQF_DISABLED' undeclared (first use in this function)
make[3]: *** [/home/mader/v4l-dvb/v4l/ivtv-driver.o] Error 1
make[2]: *** [_module_/home/mader/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mader/v4l-dvb/v4l'
make: *** [all] Error 2

---

### Post by david_2001 on 2007-03-04
> **MadeR said:**
> :mad: :roll:  
does anybody know whether is there or not a stable branch for this dvb/v4l project? (I'm starting to miss FreeBSD STABLE(tested and functioning before commitment)/UNSTABLE way of doing things)

...

By coincidence, the compilation problem with the ivtv driver was fixed in the v4l-dvb development tree about 3 hours ago as I write this.  If you download the v4l-dvb source again you should find that it compiles without error (it does for me).

---

### Post by MadeR on 2007-03-04
thank you :)

---


---
title: "HDTV install"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by cotodd on 2006-12-13
've been trying to install MythTV for 2 weeks.

Setup Pvr250 and Avertv 180.  I can get the pvr250 card working (snd & picture) using IVTV drivers.
Pvr250 works in Mythtv and I can capture video/audio and play it back on gxine.  I was able to capture video on the composite input on the Avertv 180 but no sound.  In trying to troubleshoot the
problem, I decided to start fresh and concentrate only on the Avertv 180 card (no Mythtv).  I loaded the nxt2004.fw and cp to /lib/firmware. I did not install IVTV but did install all dvb-libs.

dmesg 

[17179596.428000] saa7133[0]: found at 0000:04:07.0, rev: 209, irq: 66, latency: 64, mmio: 0xfebff800
[17179596.428000] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[17179596.428000] saa7133[0]: board init: gpio is 110400
[17179596.564000] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179596.564000] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[17179596.564000] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[17179596.564000] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[17179596.564000] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[17179596.564000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179596.564000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179596.564000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179596.564000] saa7133[0]: registered device video0 [v4l2]
[17179596.564000] saa7133[0]: registered device vbi0
[17179596.564000] saa7133[0]: registered device video0 [v4l2]
[17179596.564000] saa7133[0]: registered device vbi0
[17179596.572000] NET: Registered protocol family 17
[17179596.588000] saa7134 ALSA driver for DMA sound loaded
[17179596.588000] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 66 registered as card -1

cotodd@cotodd-myth:~$ cat /dev/video0 > /tmp/testv0.mpg
cat: /dev/video0: Input/output error


cotodd@cotodd-myth:~$ ls /dev/vi*
/dev/video  /dev/video0

cotodd@cotodd-myth:~$ ls /lib/firmware
2.6.17-10-generic  dvb-fe-nxt2004.fw

Any ideas?

---

### Post by Fully216 on 2006-12-13
You might have more luck if you post on mythtv's forum.  They also have some very smart people there, especially because the problems tends to be so specifically geared to hardware and no the distro.  Just a suggestion, not that someone couldn't help you here.

[http://www.mythtv.org/wiki/index.php/Main_Page](http://www.mythtv.org/wiki/index.php/Main_Page)
[http://www.mythtvtalk.com](http://www.mythtvtalk.com)
[http://mysettopbox.tv/phpBB2/](http://mysettopbox.tv/phpBB2/)
[http://plutohome.com/support/phpbb2/](http://plutohome.com/support/phpbb2/)

---


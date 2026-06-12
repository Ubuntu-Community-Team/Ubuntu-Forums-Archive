---
title: "TVtime + saa7130 Compro Videomate DVB-T200"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Pixus on 2007-06-28
Hi everyone, I'm new to these forums, and new to Ubuntu (and Linux as a whole).

I'm having trouble getting my TV card working with any software, I'm not sure what's wrong, and what to do next. TVtime seems the most promising software to use for my type of card (I've tried a few others, to no avail), but when I run it, all I get is a blank screen, no channels or anything.

The TV card works fine using Compro's software under Win XP.

According to this, I think my TV card (Compro Videomate DVB-T200 (saa7130 chipset)) is installed and running correctly:

```

~$ dmesg | grep saa
[   53.698279] saa7130/34: v4l2 driver version 0.2.14 loaded
[   53.698617] saa7130[0]: found at 0000:01:08.0, rev: 1, irq: 19, latency: 32, mmio: 0xe7000000
[   53.698624] saa7130[0]: subsystem: 185b:c901, board: Compro Videomate DVB-T200 [card=71,autodetected]
[   53.698635] saa7130[0]: board init: gpio is 853f51
[   53.698740] input: saa7134 IR (Compro Videomate DV as /class/input/input8
[   54.081004] saa7130[0]: i2c eeprom 00: 5b 18 01 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   54.081014] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   54.081020] saa7130[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 88 ff ff ff ff
[   54.081027] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.081033] saa7130[0]: i2c eeprom 40: ff d0 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   54.081040] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   54.081046] saa7130[0]: i2c eeprom 60: 30 26 ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.081052] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.081169] saa7130[0]: registered device video0 [v4l2]
[   54.081206] saa7130[0]: registered device vbi0
[   54.272441] saa7134 ALSA driver for DMA sound loaded
[   54.272482] saa7130[0]/alsa: saa7130[0] at 0xe7000000 irq 19 registered as card -2

```

However, when I run TVtime....

```

~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/pixus/.tvtime/tvtime.xml
/home/pixus/.tvtime/stationlist.xml: No existing PAL station list "custom".

```

Also, when I run TVtime's scanner:

```

~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/pixus/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/pixus/.tvtime/stationlist.xml: No existing PAL station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

```

I'm not sure how to do what it's telling me to do, or even if that'll fix the problem once I've done it. I've spent quite a few hours now trying out stuff I've read here, and from various Google results, blindly, but nothing is working.

Any help would be very appreciated, I'd love to get rid of XP on my computer, but without a working TV card I can't leave it (I don't have a television set, this card is all I have for watching TV.)

---

### Post by arckuk on 2007-07-29
I have had the same problem with my Compro T200. I have found through various searching and headscratching that entering:

modprobe saa7134-dvb 

at the terminal prompt allows me to use this card successfully. I am not sure of the best way to make this permanent, but I have put this command as one of the startup programs under System -> Preferences -> Sessions (otherwise it needs to be entered manually each time the system is restarted.

Hope this helps...

---

### Post by david_2001 on 2007-07-30
> **Pixus said:**
> However, when I run TVtime....

The other point to make is that tvtime is primarily an analogue TV viewer.  Try using kaffeine, which supports dvb-t, instead of tvtime.

---


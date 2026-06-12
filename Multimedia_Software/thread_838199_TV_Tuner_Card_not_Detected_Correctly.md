---
title: "TV Tuner Card not Detected Correctly"
date: 2008-06-23
forum: Multimedia Software
---

### Post by webbed on 2008-06-23
I currently have installed a Compro Technology, Inc. VideoMate T750 which uses the SAA7133/SAA7135 chipset.

The card shows up under the Multimedia Systems Selector as Unkown/Generic for the Video for Linux 2 Driver (v4l2).

I tried using TVTime to scan and setup channels but I am unable to change the device from Default.

dmesg | grep saa7133

```
[   54.696901] saa7133[0]: found at 0000:01:0a.0, rev: 209, irq: 20, latency: 32, mmio: 0xfe9ff000
[   54.696906] saa7133[0]: subsystem: 185b:c900, board: UNKNOWN/GENERIC [card=0,autodetected]
[   54.696917] saa7133[0]: board init: gpio is 84bf00
[   54.832460] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   54.832468] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   54.832474] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 03 01 08 ff 00 89 ff ff ff ff
[   54.832480] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.832486] saa7133[0]: i2c eeprom 40: ff d7 00 c4 86 1e 05 ff 02 c2 ff 01 ff ff ff ff
[   54.832491] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   54.832497] saa7133[0]: i2c eeprom 60: 30 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.832502] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.880515] saa7133[0]: registered device video0 [v4l2]
[   54.880533] saa7133[0]: registered device vbi0
[   55.491371] saa7133[0]/alsa: saa7133[0] at 0xfe9ff000 irq 20 registered as card -2

```

and

dmesg | grep saa7134

```
[55.491344] saa7134 ALSA driver for DMA sound loaded
```

[http://tvtime.sourceforge.net/problems.html#undetected]("http://tvtime.sourceforge.net/problems.html#undetected")

The TVTime Sourceforge page suggests that I check the documentation for my linux kernal for the CARDLIST.

I would like help to get the Video4Linux drivers to detect the card correctly for use.

---

### Post by ahbart on 2008-06-23
As far as I understand from your dmesg output your card is detected well. I have a tvcard myself with the same chipset, and this one is (also) working out of the box. 
What is your exact problem with it? Did you try another application?
It looks like your device is /dev/vbi0 or /dev/video0 (just to let you know).

---

### Post by webbed on 2008-06-23
At the moment I have tried the following software to try and use the card:

Me-TV
MythTV
TVTime
Xine
VLC (this will open a blank screen using /dev/video0 or /dev/vbi0)

At the moment I have tried to follow the steps on this guide to get it working through VLC, I know at the moment I should just try and get it working for one program but I've been trying as many options as possible searching through google just to get it to work.

[http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/]("http://davidwinter.me.uk/articles/2008/02/08/watching-freeview-dvb-t-tv-with-vlc-player-on-ubuntu/")

When I try to make a channels.conf file with this command I get a File or Folder not found error message

```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Brisbane -o zap | tee ~/channels.conf
```

If you have any particular steps to get it running with any application I be happy to try them out (as I don't seem to be having much luck solving it on my own).

Edit, the error I get from the above command is:

```
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```

---

### Post by webbed on 2008-07-11
*** Bump ***

---

### Post by wolfen69 on 2008-07-11
see [this]("http://www.linlap.com/wiki/Installing+the+latest+V4L+TV+tuner+drivers+for+Ubuntu+7.10") to install the latest v4l drivers. it says it's for ubuntu 7.10, but will work for 8.04.

---

### Post by webbed on 2008-07-13
Thanks for the link to the how to, Ubuntu not correct detects and Displays the name for my TV Tuner card.

TVTime now allows me to go into the Channel Management menu however for the current time constantly says there is no siganl (which there is under Windows).

The scan command mentioned above still produces the same message.

---


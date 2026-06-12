---
title: "TV for dapper drake"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by devpatel on 2006-07-13
ok this might be kinda noobish request but here it goes.

ive got a tv card with phillips chipset saa7131.
i heard that the bttv saa7134 drivers worked but i tried getting and installing them but kept failing. after frustration i looked for programs and found mythtv and a couple others.....they all contained too many dependecies and one or more of the dependies failed to install for some reason...

so is there any program with fewer dependencies that i can use. if so can u post a link to detailed installation or guide me through installing it.. thanks

my system does know theres a tv card if it helps

---

### Post by leo_m on 2006-07-13
I do not know if any programs can support your TV card without the driver having loaded first, but if you find such a program, let me know since I am suffering from the problem of my TV Card not yet supported by saa7134.

Now, you should do a :

```
dmesg | grep saa
``` 
And see if your card is detected as type -1 (means the driver is not loaded)

Also, see if the driver detects your card in the output of the above command.  If it says board: UNKNOWN/GENERIC, then your board/card is not detected.

It will be nice to see if your card is listed in the saa7134.h file (this is in kernel source, at drivers/media/video/saa7134 directory.  If not, it means your card is not yet supported officially.

---

### Post by devpatel on 2006-07-13
this is what i get
[17179597.592000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179597.592000] saa7133[0]: found at 0000:00:0d.0, rev: 209, irq: 185, latency: 32, mmio: 0xed800000
[17179597.592000] saa7133[0]: subsystem: 4e42:3306, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179597.592000] saa7133[0]: board init: gpio is 210000
[17179597.732000] saa7133[0]: i2c eeprom 00: 42 4e 06 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179597.732000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[17179597.732000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 ed ff ff ff ff
[17179597.732000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.732000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 32 15 ff ff ff ff
[17179597.732000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.732000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.732000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.732000] saa7133[0]: registered device video0 [v4l2]
[17179597.732000] saa7133[0]: registered device vbi0
[17179597.752000] saa7134 ALSA driver for DMA sound loaded
[17179597.752000] saa7133[0]/alsa: saa7133[0] at 0xed800000 irq 185 registered as card -1

What does this tell you?

PS when i said i failed installing saa7134 drivers..i mean i didnt know how to lol....:???:


u can probably guess im new to linux

---

### Post by devpatel on 2006-07-14
and another thing...is there anyway to find out if ive installed the saa7134 driver...because im not sure.....

---

### Post by leo_m on 2006-07-14
> **devpatel said:**
> and another thing...is there anyway to find out if ive installed the saa7134 driver...because im not sure.....

You can remove the loaded saa7134 driver by :

```
sudo rmmod saa7134-alsa
sudo rmmod saa7134
``` 
You can load saa7134 driver by:

```
sudo modprobe saa7134
``` 
You have saa7134 loaded, but it does not detect your card: the same predicament as mine: see [http://www.ubuntuforums.org/showthread.php?t=204095](http://www.ubuntuforums.org/showthread.php?t=204095)

As noted earlier, you can see the saa7134.h file to manually check if your card is there and tell about your finding here.  You can get kernel source using Synaptic (System|Administration|Synaptic Package Manager, then search for kernel and choose the package related to source for your kernel version).  If you wish to get the latest kernel source, just to verify if your card is supported in the latest version or not, go to [http://kernel.org](http://kernel.org) and download full source (the F hyperlink), then check the same file mentioned above there for your card's entry, if any.

If your card is not supported, you are out of luck till either someone or you yourself provide(s) a driver for the card...

---

### Post by teet on 2006-07-14
> so is there any program with fewer dependencies that i can use. if so can u post a link to detailed installation or guide me through installing it.. thanks

```
sudo apt-get install tvtime
```

TV Time is a very simple program for watching live TV.  First you should try to get your card to work with TV time...then worry about MythTV or other more advanced programs.

-teet

---


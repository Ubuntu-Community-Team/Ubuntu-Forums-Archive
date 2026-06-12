---
title: "No sound in tvtime - &quot;Can't open device /dev/mixer&quot;"
date: 2011-01-10
forum: Multimedia Software
---

### Post by Tom_AUT on 2011-01-10
Hiya!

I used to watch and record TV in Vista and Win7 with a SAA7134 capture card, and all worked fine. Using TVTime in Ubuntu 10.10 64bit (no upgrade but fresh install, everything up-to-date), I get picture but no sound. Instead I get this error message when running TVTime from the terminal: *Can't open device /dev/mixer, mixer volume and mute unavailable.*

Using lspci in terminal lists the card as following:

```
02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```And dmesg outputs this:

```
[   16.078404] saa7130/34: v4l2 driver version 0.2.16 loaded
[   16.078458]   alloc irq_desc for 17 on node -1
[   16.078460]   alloc kstat_irqs on node -1
[   16.078471] saa7134 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.078478] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 17, latency: 84, mmio: 0xfddff000
[   16.078484] saa7133[0]: subsystem: 16be:000d, board: Medion Md8800 Quadro [card=96,autodetected]
[   16.078504] saa7133[0]: board init: gpio is 0

[   16.252517] saa7133[0]: i2c eeprom 00: be 16 0d 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   16.252527] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   16.252535] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 29 02 51 96 2b
[   16.252544] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   16.252552] saa7133[0]: i2c eeprom 40: ff 28 00 c0 96 10 03 00 c0 1c fd 79 44 9f c2 8f
[   16.252560] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252568] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252576] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252584] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252592] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252600] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252609] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252617] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252625] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252633] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.252641] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

[   16.372581] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   16.542508] tda829x 0-004b: setting tuner address to 60

[   22.350178] saa7133[0]: registered device video0 [v4l2]
[   22.350226] saa7133[0]: registered device vbi0
[   22.354567] saa7134 ALSA driver for DMA sound loaded
[   22.354597] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 17 registered as card -2
[   22.420310] dvb_init() allocating 1 frontend
[   22.490174] DVB: registering new adapter (saa7133[0])
[   22.490179] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   23.120023] tda1004x: setting up plls for 48MHz sampling clock
```Being rather new to Linux (oh great, another newbie ;) ) I don't know what additional info you might need, but I'm more than happy to post everything neededd - provided you tell me how to get that info.

Cheers!

---

### Post by Tom_AUT on 2011-01-19
I really hate to bump threats, but I haven't been able to solve that problem on my own yet.

---

### Post by LMB on 2011-04-29
This is unfortunately the effect of a new bright idea by Canonical to remove a certain older sound system, on which tvtime relied. 

So far I've found those are the affected programs
* tvtime
* gnomeratio
* quake3

My solution: revert back to 10.04. This is a LTS, or "long-time support" version, which is guaranteed to work till April 2012, or the release of another LTS. Another option is to recompile kernel with OSS support, but this is relatively difficult for a newbie (not impossible, but will take a day)

---

### Post by dixonstalbert on 2011-07-30
I have posted 2 possible solutions here:

[http://ubuntuforums.org/showthread.php?p=11102119#post11102119]("http://ubuntuforums.org/showthread.php?p=11102119#post11102119")

---

### Post by critcris on 2013-02-16
[hrvooje (hrvooje-gmail)]("https://launchpad.net/%7Ehrvooje-gmail")             wrote             on 2009-11-11:                                                            [ #12]("https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770/comments/12")                                                               Here is what I did in 9.04 :
 tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

              




It works!!! ;)

---

### Post by oldos2er on 2013-02-16
Old thread closed.

---


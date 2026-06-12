---
title: "dvb-utils problems"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by peeper on 2006-12-30
Hi,

I've just performed a fresh install of Ubuntu 6.10 (Edgy) on kit that I'm going to install MyTV on.

I have two LifeView FlyDVB-T cards in a couple of the PCI slots that appear to be detected and drivers loaded okay (I think). Now the problem is that the dvb-utils tools such as scan (the only one I've tried so far) don't work. The problem appears to be that there is no [FONT="Courier New"]/dev/dvb[/FONT] directory and associated [FONT="Courier New"]adapter<x>[/FONT] subdirectories:

```
root@pvr:/dev# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Waltham
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Waltham
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
```

I'd be grateful to anyone who could explain what the real problem is here. Is it an incompatibility issue between Ubuntu 6.10 and the dvb-utils package? Or has something gone wrong during detection and configuration of the DVB-T cards?

Here's a bit more detail on my system setup...

Although [FONT="Courier New"]/dev/dvb[/FONT] is missing, there is a [FONT="Courier New"]/dev/.static/dev/dvb[/FONT] directory and associated adapter subdirectories.

The DVB-T cards show up as being detected in the /var/log/messages file:

```
Dec 30 13:33:29 pvr kernel: [17179585.288000] saa7134[0]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
Dec 30 13:33:29 pvr kernel: [17179585.288000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input3
Dec 30 13:33:29 pvr kernel: [17179585.424000] saa7134[1]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
Dec 30 13:33:29 pvr kernel: [17179585.424000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input4

```

Grepping lsmod output shows that modules are loaded for the DVB-T card's saa7134 chipset: 
```
saa7134_alsa           15392  0
saa7134               118496  1 saa7134_alsa
video_buf              27652  2 saa7134_alsa,saa7134
compat_ioctl32          2432  1 saa7134
v4l2_common            17280  1 saa7134
v4l1_compat            15108  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              28548  2 saa7134,ir_kbd_i2c
snd_pcm                84612  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
videodev               10752  1 saa7134
i2c_core               23424  4 i2c_ec,saa7134,nvidia,ir_kbd_i2c
snd                    58372  9 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

```

The version of dvb-utils is 1.1.1-2 and this was obtained from the Ubuntu universe/misc repositories.

Thanks,

Peeper.

---

### Post by pseudonym on 2006-12-30
dvb-utils is working fine on edgy here. but I've only got 1 card, though ;)

Yours is a well supported card. Is that all the syslog output you get? On mine I also get messages about frontends being registered...

---

### Post by peeper on 2006-12-30
Hiya,

I do have more syslog output, but I think the stuff I didn't post is a duplicate of the stuff I did post. For completeness, here's the syslog output that I find:
```
root@pvr:/dev# grep DVB /var/log/messages
Dec 29 23:02:13 pvr kernel: [17179586.184000] saa7134[0]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
Dec 29 23:02:13 pvr kernel: [17179586.184000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input3
Dec 29 23:02:13 pvr kernel: [17179586.324000] saa7134[1]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
Dec 29 23:02:13 pvr kernel: [17179586.324000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input4
Dec 30 13:33:29 pvr kernel: [17179585.288000] saa7134[0]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
Dec 30 13:33:29 pvr kernel: [17179585.288000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input3
Dec 30 13:33:29 pvr kernel: [17179585.424000] saa7134[1]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
Dec 30 13:33:29 pvr kernel: [17179585.424000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input4

``` 

I also grep'd on for the term 'front' in /var/log/messages but found no results.

I'm not that familiar with DVB on Linux. What are the front-end details that are included in your syslog? Is the absence of front-end details from my syslog a potential source of the problems I'm seeing?

Any more ideas?

Thanks,

Peeper.

---

### Post by peeper on 2006-12-30
Also here's the grep'd output from dmesg, filtering on saa:
```
root@pvr:/dev# dmesg | grep saa
[17179584.600000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179585.288000] saa7134[0]: found at 0000:03:0c.0, rev: 1, irq: 201, latency: 64, mmio: 0xfeaff400
[17179585.288000] saa7134[0]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
[17179585.288000] saa7134[0]: board init: gpio is 10000
[17179585.288000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input3
[17179585.424000] saa7134[0]: i2c eeprom 00: 68 51 01 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179585.424000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[17179585.424000] saa7134[0]: i2c eeprom 20: 01 40 01 02 03 ff 01 03 08 ff 01 08 ff ff ff ff
[17179585.424000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.424000] saa7134[0]: i2c eeprom 40: ff 1b 00 c0 ff 10 01 01 ff ff ff ff ff ff ff ff
[17179585.424000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.424000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.424000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.424000] saa7134[0]: registered device video0 [v4l2]
[17179585.424000] saa7134[0]: registered device vbi0
[17179585.424000] saa7134[1]: found at 0000:03:0d.0, rev: 1, irq: 217, latency: 64, mmio: 0xfeaff000
[17179585.424000] saa7134[1]: subsystem: 5168:0301, board: LifeView FlyDVB-T / Genius VideoWonder DVB-T [card=86,autodetected]
[17179585.424000] saa7134[1]: board init: gpio is 10000
[17179585.424000] input: saa7134 IR (LifeView FlyDVB-T / as /class/input/input4
[17179585.560000] saa7134[1]: i2c eeprom 00: 68 51 01 03 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179585.560000] saa7134[1]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[17179585.560000] saa7134[1]: i2c eeprom 20: 01 40 01 02 03 ff 01 03 08 ff 01 08 ff ff ff ff
[17179585.560000] saa7134[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.560000] saa7134[1]: i2c eeprom 40: ff 1b 00 c0 ff 10 ff ff ff ff ff ff ff ff ff ff
[17179585.560000] saa7134[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.560000] saa7134[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.560000] saa7134[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179585.560000] saa7134[1]: registered device video1 [v4l2]
[17179585.560000] saa7134[1]: registered device vbi1
[17179585.584000] saa7134 ALSA driver for DMA sound loaded
[17179585.584000] saa7134[0]/alsa: saa7134[0] at 0xfeaff400 irq 201 registered as card -1
[17179585.584000] saa7134[1]/alsa: saa7134[1] at 0xfeaff000 irq 217 registered as card -1

``` 

Thanks,

Peeper.

---

### Post by pseudonym on 2006-12-30
Hi Peeper,

Bearing in mind that I've never owned your model card, superficially, that all looks OK - your cards are being detected and modules appear to get loaded. But...

I think your inability to scan may have something to do with the fact that the saa7134 driver is a v4l1 module which sometimes has compatibility issues with the v4l2 API. I could be wrong, but what appears to be getting loaded are only the saa7134 analogue modules, not the dvb one (card names notwithstanding). This is probably why you can't find /dev/dvb (but you can find /dev/video0 & /dev/video1, right?). The question, of course, is why?

As is often the case, the [Gentoo Wiki]("http://gentoo-wiki.com/") has something which may at least be a [clue]("http://gentoo-wiki.com/index.php?title=HARDWARE_saa7134#Enable_DVB-T") as to what's going on. I'm no DVB guru either, and the problems this wiki mentions may well have been cleared up by now in the kernel (I'm assuming you're using the default Ubuntu kernel). But it at least gives you some possibilities for loading the modules differently (in Debian-based distros this would be via a file /etc/modprobe.d/saa7134) and, perhaps best of all, the email of the module's developer :) (also, in case you don't know, [Linux TV]("http://www.linuxtv.org/") is also a good place to get help with this stuff, too).

HTH :)

---

### Post by peeper on 2007-01-03
Thanks for that pseudonym! I've been over to linuxtv.org and ended up going over to their irc channel #linuxtv where someone kindly suggested a modprob of saa7134-dvb. That seemed to do the trick and as you suggested, it appears that there are some problems with v4l2 using the module saa7134 - I'm not sure what the root cause of those the problems is (i.e. why the /dev/dvb/adapter<x> directories don't get created).

Peeper.

---

### Post by pseudonym on 2007-01-03
Cool :) Maybe someone at linux tv might write a small patch to address that, although if the issue is solved as easily as loading saa7134-dvb at startup (via /etc/modules presumably) then you won't need to bother rebuilding your kernel if and when the patch becomes available.

---


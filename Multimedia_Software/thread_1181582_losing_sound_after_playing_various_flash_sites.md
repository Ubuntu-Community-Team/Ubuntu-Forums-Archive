---
title: "losing sound after playing various flash sites"
date: 2009-06-08
forum: Multimedia Software
---

### Post by jocika011 on 2009-06-08
It's not very consistent, but I'm losing sound after playing various flash sites, ie. youtube.

I have to do restart in order to get my sound back.

do you have any solution for this?

[IMG]http://i278.photobucket.com/albums/kk102/jocika022/Screenshot-7.png[/IMG]

**_aplay -l_**

spiridon@spiridon-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
spiridon@spiridon-desktop:~$
spiridon@spiridon-desktop:~$

____________________________________________

[B][U]$ sudo cat /dev/sndstat
[/U][/B]
spiridon@spiridon-desktop:~$ sudo cat /dev/sndstat
[sudo] password for spiridon:
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux spiridon-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Live! 7.1 24bit [SB0413] at 0xdf20 irq 22
USB Device 0x46d:0x992 at usb-0000:00:1d.7-3, high speed

Audio devices:
0: CA0106 (DUPLEX)
1: USB Audio

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: CA0106 MPU-401 (UART)

Timers:
31: system timer

Mixers:
0: mixer00
1: USB Mixer

---


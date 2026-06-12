---
title: "No sound at all ICH5"
date: 2011-06-04
forum: Multimedia Software
---

### Post by fr0sty on 2011-06-04
Running Xubuntu 11.04 on an hp a250n. It has integrated audio, but I have no audio working in linux. Checked to make sure it was unmuted and tried all devices in sound preferences. a "aplay -l" command turns up this:

> frosty@Xubuntu-Frost:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
frosty@Xubuntu-Frost:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC650F at irq 17


and a "lspci -v" command returned this:
> 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8095
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=256]
	I/O ports at d400 [size=64]
	Memory at fe77f800 (32-bit, non-prefetchable) [size=512]
	Memory at fe77f400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

Now it looks like the integrated sound card is found... but I am unsure of what to do next. any help will be deeply appreciated. I bet its probably something simple, but Im not sure. Thanks.

---

### Post by Toz on 2011-06-04
Running this command in a terminal window and posting back the link to the response will be helpful information for someone to assist with troubleshooting.```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
```

Also, troubleshooting pages available at: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by fr0sty on 2011-06-04
Well heres the link to the alsa code i ran. 

[http://www.alsa-project.org/db/?f=718008bc26627135f576f482e8f47c69c7f55a64](http://www.alsa-project.org/db/?f=718008bc26627135f576f482e8f47c69c7f55a64)

Also what profile do I use for my device? see the picture for my choices... maybe i have the wrong choice selected.

---

### Post by Toz on 2011-06-04
> **fr0sty said:**
> Checked to make sure it was unmuted 
Did you check this through alsamixer? (open a terminal window, type in alsamixer, and check that all devices are unmuted? (see: [http://en.wikipedia.org/wiki/Alsamixer](http://en.wikipedia.org/wiki/Alsamixer)

---


---
title: "Linksys WGA600N Gaming Adapter"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by N1nj4turtl3 on 2011-09-01
Hi all! 

I am having trouble connecting my network adapter to my router in Ubuntu 10.04. It connects fine in windows 7 but when I dual boot over it's not even detecting any routers.

I've tried several tricks through terminal and whatnot and changed a million settings that I have read about online while googling, and my drivers are up to date, but nothing seems to work. 

The adapter plugs into the computer via ethernet then connects to the router wirelessly, so I'm not sure if this is causing problems from the computer thinking its a wired connection or something? No clue.

If anyone has any ideas, let me know. Any help is appreciated!

---

### Post by wildmanne39 on 2011-09-02
Hi, you can look at this link post 9 tells how to set it up.
[http://ubuntuforums.org/showthread.php?t=1113482&highlight=WGA600N](http://ubuntuforums.org/showthread.php?t=1113482&highlight=WGA600N)
Thank you

---

### Post by N1nj4turtl3 on 2011-09-02
I may have missed something but all it says he did was plug it in and it worked. 

Anyone have any other ideas?

---

### Post by wildmanne39 on 2011-09-02
Hi, it says he configured it in windows then plugged it in to ubuntu, I do not know how that worked but did you configure it with windows?

---

### Post by N1nj4turtl3 on 2011-09-02
Yeppers. I have everything configured in Windows and it works fine in Windows. But in Ubuntu it says connected with Wired Eth0, but my adapter is not connecting.

---

### Post by praseodym on 2011-09-02
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by N1nj4turtl3 on 2011-09-02
```
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
	Kernel driver in use: sis190
	Kernel modules: sis190
```

```
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203310  1 
snd_usb_audio          75765  2 
snd_usb_lib            15801  1 snd_usb_audio
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
joydev                  8708  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  21 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
usbhid                 36110  0 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
led_class               2864  0 
soundcore               6620  1 snd
hid                    67032  1 usbhid
nvidia               9961216  38 
parport_pc             25962  1 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
sis190                 14852  0 
mii                     4381  1 sis190
sis_agp                 4047  0 
agpgart                31724  2 nvidia,sis_agp
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            39425  1 
ohci1394               26950  0 
floppy                 53016  0 
ieee1394               81181  1 ohci1394
sata_sis                3332  2 
```

---

### Post by praseodym on 2011-09-02
Ok, additionally

```
lsusb
```

---

### Post by N1nj4turtl3 on 2011-09-03
> **praseodym said:**
> Ok, additionally

```
lsusb
```


```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c52f Logitech, Inc. 
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c22d Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 046d:0a0b Logitech, Inc. 
Bus 001 Device 006: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---


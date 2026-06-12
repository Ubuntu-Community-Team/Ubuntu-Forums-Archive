---
title: "Acer Crystal Eye Webcam Not Working"
date: 2011-05-09
forum: Multimedia Software
---

### Post by Psychv4 on 2011-05-09
[B]OS: Linux Ubuntu 11.04
Machine: Acer Inspire 4730z[/B]

my webcam isnt working and i've done everything i could think of. I installed the v4l drivers and they installed perfectly and still it doesnt work.

```
psych@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```my camera is the Suyin Corp. now then, i looked up the list of supported devices for the uvc drivers and my camera is on there. so i built the v4l device driver because my camera comes up as V4L2. so I just made that assumption to do so. and still no, I'm trying to use the camera for an in-browser site called stickam. anyway, so the drivers are definitely there.

```
psych@ubuntu:~$ ls -l /dev/v4l
total 0
drwxr-xr-x 2 root root 60 2011-05-09 05:50 by-id
drwxr-xr-x 2 root root 60 2011-05-09 05:50 by-path
psych@ubuntu:~$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2011-05-09 05:50 /dev/video0

```so if anyone could help, i would really appreciate it.

edit1:

```
psych@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
joydev                 17606  0 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336693  1 
rt2860sta             543010  0 
snd_hda_intel          33211  4 
uvcvideo               71391  0 
arc4                   12529  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
videodev               96656  1 uvcvideo
snd_pcm                96625  3 snd_hda_intel,snd_hda_codec
media                  21344  1 videodev
snd_seq_midi           13324  0 
rt2800pci              18535  0 
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
rt2x00pci              14322  1 rt2800pci
snd_rawmidi            30486  1 snd_seq_midi
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
fglrx                2739144  142 
snd_timer              29602  2 snd_pcm,snd_seq
psmouse                73535  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    16728  1 videodev
serio_raw              13166  0 
jmb38x_ms              17596  0 
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
memstick               16520  1 jmb38x_ms
snd                    67382  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
r8169                  48022  0
```

if you notice in the above terminal output to the lsmod command, v4l2_compat_ioctl32 is what i assume to be my camera, its being used by videodev and videodev is being used by uvcvideo but uvcvideo, the driver i NEED to use is being use by nothing -.-

idk if this is the problem or im just really dumb because im just a newbie at this. i really have no clue what i should do to get my cam running, but if you can help me thatd be great.

---

### Post by no2498 on 2011-05-09
open a terminal type dmesg click enter
did it make a cam grabber



also seen this a few days ago


BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)


sudo rmmod uvcvideo
sudo modprobe uvcvideo

---


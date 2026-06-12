---
title: "Need help getting back my sounds on Ubuntu 10.04"
date: 2012-03-30
forum: Multimedia Software
---

### Post by majnun90 on 2012-03-30
Alright so i recently bought a new soundcard for my old HP 061 and installed it but i cant get the sound working. I have a Xonar DG soundcard, and it detects it and all that but when i type in **alsamixer **in the command line it doesn't have the right settings in it :confused:
I put the screenshot of the window in this. Also i have got all the right versions of the drivers & i've re-installed everything but it wont work.. Please someone help me ???

---

### Post by Yellow Pasque on 2012-03-30
More info, please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by majnun90 on 2012-03-30
Here you go:
[http://www.alsa-project.org/db/?f=4df4c2b0924ef3c3e57fa657d548350a85a4f3da](http://www.alsa-project.org/db/?f=4df4c2b0924ef3c3e57fa657d548350a85a4f3da)

---

### Post by Yellow Pasque on 2012-03-30
EDIT: NVM. I see that's line in.

Are you sure it's not muted?
```
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture -24 - 24
  Front Left: Capture -24 [0%] [off]
  Front Right: Capture -24 [0%] [off]
```

---

### Post by majnun90 on 2012-03-30
Yeah thats the problem, i dont remember how but it said that its muted and i should check alsamixer so i did and i got this, but in the sound preferences everything is unmuted :S

---

### Post by majnun90 on 2012-03-31
I would really appreciate it if someone would try to tell me what's the problem... Since im not an expert with Ubuntu. I will post any information you need just let me know , thanks in advance guys

---

### Post by majnun90 on 2012-04-02
Okey so since nobody is willing to help me, i'll post some things i have tried to do.
I tried to change some lines in  **/etc/modprobe.d/alsa-base.conf **file, but im not really sure which ones are the correct lines 
This wat i have in that file now:


```
 # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=basic
```
[SIZE=2]I really need the help guys i'm starting to sound desperate but this is driving me crazy ! 
I don't want to buy a new computer just yet...[/SIZE]

---

### Post by majnun90 on 2012-04-08
**Alright i think i found the problem here... I realized that theres the driver CD that came with the soundcard, but when i put it in i have no idea what i should do :S**
[B]
Its for windows obviously and i think the problem with the sounds should be solved when i install the driver so... If anyone has a solution for this then please, PLEASE tell me. Thanks in advance :-?[/B]

---

### Post by Yellow Pasque on 2012-04-08
Unless you run Windows, a Windows driver CD is useful only as a coaster/frisbee. I suggest you try a different PCI slot and/or another OS (Ubuntu 11.10 or 12.04 LiveCD/USB should work) to verify the hardware is good. I actually have a Xonar DG as my spare sound card, and have never had issues with output as long as I was using ALSA 1.0.24 or later. 

Note: please use the default font. Bolding the whole post defeats the point of bolding and doesn't help readability for those who aren't vision-impaired (and those who are use their own custom fonts).

---

### Post by majnun90 on 2012-04-11
Yeah i think i'll have to switch to Windows and install it there and then just put back Ubuntu... Thanks for the help.

---


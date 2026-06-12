---
title: "Problem - No Sound on HDMI output (HP DV9348ea)"
date: 2009-08-16
forum: Multimedia Software
---

### Post by zoroastre99 on 2009-08-16
Hi,

Sound on HDMi begins to work out of the box for new configurations, but I can't find a way to make it work on my laptop (HP DV9348ea), despite many days of web crawling.

basicaly the system is made of:
- Intel Core Duo,
- NVidia 7600 chip
- Conexant Sound chip

I have Nvidia "180" driver, and HDMI works fine as far as video is concerned on a Samsung TV. Detection of HDMI features is even OK.

Alsa is 1.0.18, and Sound is OK for playback on the laptop (internal speakers, external jacks). 
The tests are done by using Totem 2.26.1 as a video reader.

IEC958 is checked in volume control applet for HDA Intel (Alsa mixer).

Since I still have Vista on a dual boot, I can test that on a HW point of view, it is possible to redirect the sound on the HDMI output. On Vista, It's necessary to select SPIDF as "default output" to activate HDMI, so it maybe not so easy to make it work on ubuntu.

> gerard@gerard-ubuntu:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : CONEXANT Analog [CONEXANT Analog]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : Conexant Digital [Conexant Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0> gerard@gerard-ubuntu:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)> gerard@gerard-ubuntu:~$ uname -r
2.6.28-15-generic> gerard@gerard-ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)> gerard@gerard-ubuntu:~$ lspci
...
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
...
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)> gerard@gerard-ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xde300000 irq 22

gerard@gerard-ubuntu:~$ cat /proc/asound/modules
 0 snd_hda_intel

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```I've tested an upgrade to Nvidia 185 driver, but the installation through the "run" file downloaded from Nvidia site made quite a mess on the system (GLX was unable to activate correctly with the X Server) so I've suppressed & reinstalled the 180 driver through synaptic, and suppresed all traces from the 185 installation (files deleted, links to 180 remade) thanks to a post on similar trouble ...

Any help will be welcomed, I'm not that familiar with ubuntu so far, and maybe someone can guide me on this issue.

Regards.

---


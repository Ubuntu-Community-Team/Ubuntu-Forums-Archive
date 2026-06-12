---
title: "[LINUX] - Problem with AC3 PassThrough/XBMC/ALSA"
date: 2010-03-25
forum: Multimedia Software
---

### Post by tooney on 2010-03-25
Hello !!!

First of all, I want to warn you and apologize for my poor english, coz' I'm french :;):

I have an annoying issue to make my soundcard work. I know this problem was many times discussed, but I wasn't able to solve it. I search for one week, but it doesn't work! It makes me crazy :sniffle:

So here is my configuration :

> Motherboard : Asus P5Q3 Deluxe
Soundcards : Onboard Intel HDA - Theatron Agrippa DTS (Club3D)
System : Linux 9.10 (minimal install) + XBMC 9.11
A/V Receiver : Onkyo TX-SR 607 (connected with coaxial cable)I installed minimal XBMCbuntu with following [this tuto]("http://wiki.xbmc.org/index.php?title=XBMCbuntu").
Everything seemed to work well, and I tried to watch a video :

[LIST]
[*]Video with mp3 encoded : output only on the front speakers
[*]Video with AC3 encoded : ouptut only on the front speakers
[/LIST]


I tried many installations / configurations :

[LIST]
[*]With my two soundcards activated
[*]Only with the onboard card activated
[*]Only with the Theatron card activated
[/LIST]


But the result was the same... :blush:

I did many searches on the web, and I tried many and many solutions...

I decided to make basical tests with aplay and mplayer. I have downloaded on [this site]("http://www.lynnemusic.com/") an [AC3 file]("http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3") who plays alternatively on each speaker (front right, front center, front left, rear left, rear right) :

```
mplayer -ao alsa:device=plughw=0.2 -ac hwac3 www_lynnemusic_com_surround_test.ac3
```or :
```
mplayer -ao alsa:device=plughw=1.1 -ac hwac3 www_lynnemusic_com_surround_test.ac3
```for playing sound with each card on each speaker. I only had sound with my front speakers... Same thing in XBMC...

So I made still more changes (that I can't remember... I think I played with "iecset audio") and I saw a change in XBMC :

[LIST]
[*]Video files with stereo sound were played on every speaker with a perfect sound! (I thought) Yep !!! (when configuring my A/V Receiver in format "Pure Audio")
[*]But for video in AC3, no sound at all, and auto-select of the A/V Receiver switches from DTS to no DTS to DTS to no DTS ...
[/LIST]


When launching the same commands with mplayer and AC3, I can only hear "crackling" in the front speakers. No sound rear...

I tried to upgrade my alsa version with [this script]("http://ubuntuforums.org/showthread.php?p=6589810") (from 1.0.20 to 1.0.22.1). Same result!

I haven't tested for the moment, but I have a dual-boot with Windows XP on this computer. So I will test the AC3 file to see if I obtain the same result.

Here are details about my installation :

**cat /proc/asound/cards**

```
user@pchc:~$ cat /proc/asound/cards
 0 [CMI8770        ]: CMI8738-MC8 - C-Media CMI8770
                      C-Media CMI8770 at 0xe800, irq 10
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 21

```**aplay -l**

```
user@pchc:~$ sudo aplay -l
**** Liste des PLAYBACK pÃ©riphÃ©riques ****
carte  0: CMI8770 [C-Media CMI8770], pÃ©riphÃ©rique 0 : CMI8738-MC8 [C-Media PCI DAC/ADC]
  Sous-pÃ©riphÃ©riques: 1/1
  Sous-pÃ©riphÃ©rique: #0: subdevice #0
carte  0: CMI8770 [C-Media CMI8770], pÃ©riphÃ©rique 1 : CMI8738-MC8 [C-Media PCI 2nd DAC]
  Sous-pÃ©riphÃ©riques: 1/1
  Sous-pÃ©riphÃ©rique: #0: subdevice #0
carte  0: CMI8770 [C-Media CMI8770], pÃ©riphÃ©rique 2 : CMI8738-MC8 [C-Media PCI IEC958]
  Sous-pÃ©riphÃ©riques: 0/1
  Sous-pÃ©riphÃ©rique: #0: subdevice #0
carte  1: Intel [HDA Intel], pÃ©riphÃ©rique 0 : AD198x Analog [AD198x Analog]
  Sous-pÃ©riphÃ©riques: 1/1
  Sous-pÃ©riphÃ©rique: #0: subdevice #0
carte  1: Intel [HDA Intel], pÃ©riphÃ©rique 1 : AD198x Digital [AD198x Digital]
  Sous-pÃ©riphÃ©riques: 1/1
  Sous-pÃ©riphÃ©rique: #0: subdevice #0

```**aplay -L**

```
user@pchc:~$ sudo aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output

```**cat /etc/modprobe.d/alsa-base.conf**

```
user@pchc:~$ cat /etc/modprobe.d/alsa-base.conf
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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

```Any help would be welcomed because I'm a little lost...


Tooney.

---

### Post by Azzir on 2010-08-31
Hi Tooney :D

How did you go with this? I have the P5Q3 deluxe also, and when I try to get audio output from the coax S/PDIF output under Ubuntu 10.04 I fail every time :-(

Any help would be greatly appreciated!

Azzir (Ryan)

---

### Post by papibe on 2010-09-02
It is possible that some of the speakers are muted. Try:
```
$ alsamixer -c 0
```
to check both the mute status and the volume of each output (change 0 for 1 for the other card).

After that you could try:
```
$ speaker-test -Dsurround51 -c6 -twav
```
or
```
$ speaker-test -Dplug:surround51 -c6 -twav
```
to test each speaker individually.

Good luck!

---

### Post by Azzir on 2010-09-06
Thanks papibe, I'll check when I get home :-)

---


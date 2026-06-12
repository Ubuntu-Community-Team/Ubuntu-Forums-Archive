---
title: "ALSA digital passthrough hissing, scratching, cracking noise"
date: 2011-01-21
forum: Multimedia Software
---

### Post by michikommader on 2011-01-21
Hey,

I am already searching for a week without success.


[LIST]
[*]Thinkpad T61
[*]Coaxial S/PDIF through docking station
[*]Ubuntu 10.04/10.10
[/LIST]
Normal stereo through IEC958 with PulseAudio using the S/PDIF works fine. But *everything* comes out as stereo. But when wanting to use AC3 digital passthrough for DTS/DD5.1 sound files my receiver only outputs a loud hissing, scratching noise. This gets really annoying!

In VLC or MPlayer I use ALSA  passthrough as output via **HDA Intel: AD198x Digital (hw:0,1)** which is the digital out of my sound card.

[B]cat /proc/asound/cards
[/B]```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe220000 irq 48
 1 [Em28xxAudio    ]: Em28xx-Audio - Em28xx Audio
                      Empia Em28xx Audio
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 7KHT24WW-1.08
```[B]aplay -l
[/B]```
Karte 0: Intel [HDA Intel], Gerät 0: AD198x Analog [AD198x Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: AD198x Digital [AD198x Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
```[B]aplay -L
[/B]```
default
pulse
    Playback/recording through the PulseAudio sound server
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
dmix:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Hardware device with all software conversions
```[B]cat /etc/modprobe.d/alsa-base.conf
[/B]```
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
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=thinkpad
```The thing is that this all worked in 8.10 and 9.04. Then I freshly installed 10.4 and this problem remains still in 10.10. I suppose that some audio codec/plugin interferes the clear unprocessed passthrough which results in this bloody noise.  But with a Live-CD of 9.04 for example, I don't get it to work again neither. *shrug*

Please help me, I am really desperate ;)

Greets, Michi

---

### Post by michikommader on 2011-02-01
Finally it seems to work after uninstalling packages **libxvidcore4** and** libavcodec-extra-52**.
No hissing/scratching any more, just pure pass-through!

Greets, Michi

---


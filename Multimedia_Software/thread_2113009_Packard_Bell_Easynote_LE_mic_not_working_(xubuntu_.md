---
title: "Packard Bell Easynote LE mic not working (xubuntu 12.04)"
date: 2013-02-06
forum: Multimedia Software
---

### Post by worksmart on 2013-02-06
hi all,

The microphone of my Packard Bell Easynote LE on Xubuntu 12.04 does not work. For example, neither :

```

$ arecord -vv -f cd -t wav sample.wav

```or the skype test sound does not record any sound. I tried to :

-purge and reinstall pulseaudio
-upgrade alsa 

but it is still the same. Here are some diagnostics of my system I found on :
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1) and :
[http://ubuntuforums.org/showthread.php?t=1548340](http://ubuntuforums.org/showthread.php?t=1548340)

Here are the outputs (in French, sorry) :  

```

$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Generic [HD-Audio Generic], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: Generic_1 [HD-Audio Generic], périphérique 0: CONEXANT Analog [CONEXANT Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
``````

$ lspci -nn | grep '\[04[80][13]\]' 
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)

``````

$ uname -r
3.2.0-35-generic

``````

$ dpkg -l alsa-info.sh
Aucun paquet ne correspond à alsa-info.sh.

``````

$ lspci -nn | grep Audio
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)

``````

$ cat /proc/asound/card0/codec#0
Codec: ATI R6xx HDMI

``````

$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 3]: digital audio playback
  3: [ 0- 0]: hardware dependent
  4: [ 0]   : control
  5: [ 1- 0]: digital audio playback
  6: [ 1- 0]: digital audio capture
  7: [ 1- 2]: hardware dependent
  8: [ 1]   : control
 33:        : timer

``````

$ cat /etc/modprobe.d/alsa-base.conf
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

``````

$ grep -e audio /etc/group
audio:x:29:pulse,edrisse

``````

$ hwinfo --sound
tests: 8: tests: hwinfo: not found

```Thank you very much for your help

---


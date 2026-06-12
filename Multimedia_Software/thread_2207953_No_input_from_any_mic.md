---
title: "No input from any mic"
date: 2014-02-25
forum: Multimedia Software
---

### Post by acg2 on 2014-02-25
My system no longer records any audio from the laptop's internal microphone. I can't even record static!
External microphones also do not work. I've tried all the suggestions that I could find in other threads.

Running lubuntu 12.04.04 on a Thinkpad X200.

# uname -a
Linux name-Thinkpad 3.2.0-59-generic-pae #90-Ubuntu SMP Tue Jan 7 23:07:06 UTC 2014 i686 i686 i386 GNU/Linux

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.

# head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20561 (Hermosa)

this is the content of my alsa-base.conf
[SIZE=2]```
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

options snd-hda-intel position_fix=1
options snd-hda-intel model=thinkpad
```[/SIZE]

These are my alsamixer settings.
[IMG]http://i57.tinypic.com/2yyqghu.jpg[/IMG]

Any help would be greatly appreciated!

---

### Post by Yellow Pasque on 2014-02-26
Have you tried "model=lenovo-x200" intead of "model=thinkpad"  (Note: in newer kernels, no model override should be necessary)
model=thinkpad is for a different Conexant codec

---

### Post by acg2 on 2014-02-26
No luck with "model=lenovo-x200"
Oddly, I've gotten Audacity to record some static-ey noise, but only for a fraction of a second, and only immediately after I adjust certain settings or force reload alsa.
[IMG]http://i59.tinypic.com/qrx2z9.png[/IMG]

---

### Post by acg2 on 2014-03-01
Oh actually, that did help my external mic work!
The internal one still does not work, though. Do you have any suggestions about how I might determine whether this is a hardware or a software issue?

Thank you!

---

### Post by mörgæs on 2014-03-02
A live boot of Lubuntu 13.10 might give an indication.

---


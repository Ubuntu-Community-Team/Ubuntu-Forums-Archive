---
title: "No Sound"
date: 2011-02-05
forum: Multimedia Software
---

### Post by D-Tre on 2011-02-05
I've google'd this problem for hours today and just cant seem to get it to work with any of the solutions I've found. I updating from 10.10 to 11.04 about 3 hours ago thinking it might help but it didn't. I know I've heard the Ubuntu jungle theme thing when you login at least once but haven't heard anything in a few days. 

I'm not sure what sort of information you guys may need on this because I'm really not that advanced with Ubuntu yet. So please, if anyone could help just let me know what you need or what commands to run.

If it matters at all, I'm on a Dell Inspiron 580 -64 bit. :lolflag:

---

### Post by coosadog on 2011-02-05
I have the same problem. New 10,10 install. Here's my info, which all looks good to me. (not muted, btw):

tom@tom-desktop:~$ uname -a
Linux tom-desktop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
tom@tom-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tom@tom-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
tom@tom-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC662 rev1

**Some more info**

modprobe.d:

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

---

### Post by D-Tre on 2011-02-05
Anyone?

---

### Post by lyall on 2011-02-05
have look to see if it is muted?
from the System > Preference > Sound
in the Sound Preference window see if the mute is checked for the Output volume or if it to the far left

also check the Input tab the see if the mute is checked 

good luck and have fun learning

---


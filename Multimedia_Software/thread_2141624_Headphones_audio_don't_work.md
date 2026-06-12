---
title: "Headphones audio don't work"
date: 2013-05-03
forum: Multimedia Software
---

### Post by Jumbaro on 2013-05-03
Hello everyone, i have installed xubuntu and it's all okey, but the sounds/audio don't work in the headphones also if are recognized by the system. Help pls

Here there are some useful informations:
Version: 13.04
Result of lspci | grep -i audio
```

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)

```
Result of aplay -l
```

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 0: ALC892 Analog [ALC892 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 1: ALC892 Digital [ALC892 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 9: HDMI 3 [HDMI 3]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```
Result of cat /proc/asound/card0/codec* | grep Codec 
```

Codec: Realtek ALC892

```
And the alsa-base.conf configuration
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
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

Also alsa versions
```


ii  alsa-base                            1.0.25+dfsg-0ubuntu4                all              ALSA driver configuration filesii  alsa-utils                           
1.0.25-4ubuntu2                     i386         Utilities for configuring and using ALSA
ii  bluez-alsa:i386                      4.101-0ubuntu8b1                    i386         Bluetooth ALSA support
ii  gstreamer0.10-alsa:i386              0.10.36-1.1ubuntu1                  i386         GStreamer plugin for ALSA
```
I hope in you penguins :KS

---

### Post by doug-ravennasprings on 2013-10-15
I have nearly the identical problem. 
It seems I have analog audio but no digital.
Most of my data is identical to the above.
I have yet to find a solution though I do hear there are problems with  Ubuntu sound before 13.10.

---


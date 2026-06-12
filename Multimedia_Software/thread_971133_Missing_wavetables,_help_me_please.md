---
title: "Missing wavetables, help me please"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Ter Rymon on 2008-11-04
I have a SE440BX-2 motherboard with a built in Yamaha sound card.

When I type 

aplay -l 

into terminal I get the following:

```
card 0: YMF740C [Yamaha DS-1L (YMF740C)], device 0: YMFPCI [YMFPCI]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: YMF740C [Yamaha DS-1L (YMF740C)], device 1: YMFPCI - IEC958 [YMFPCI - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: YMF740C [Yamaha DS-1L (YMF740C)], device 2: YMFPCI - Rear [YMFPCI - Rear PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

NOTICE the 32 subdevices that should be wavetables BUT

when I type in 

aplaymidi -l

I get :

```
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    Yamaha DS-1L (YMF740C)           Yamaha DS-1L (YMF740C) MIDI
 17:0    OPL3 FM synth                    OPL3 FM Port

```

NO WAVETABLES --- How do I fix; sound and midi play back are working but cannot load sf2 files nor can i use midi devices 

in /etc/modules is the following:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
snd-sbawe
snd-emu8000-synth
```

If I try to change snd-sbawe to snd-ymfpci I get no sound.
If I add snd-ymfpci I get no sound.

in /etc/modprobe.d/alsa-base is the following:

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
# enable Yamaha midi and etc
options snd-ymfpci mpu_port=0x330 fm_port=0x388 joystick_port=1 
# rear_switch=1
```

Any suggestions would be helpful

---

### Post by Ter Rymon on 2008-11-05
New problem has happened... I am using 8.10 Intrepid which just updated some files which busted a lot of my apps:

The following will not load:

Ekiga


May just backup and do fresh install at this point....

---


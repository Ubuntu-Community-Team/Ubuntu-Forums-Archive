---
title: "No Sound with HDA ATI SB"
date: 2008-06-26
forum: Multimedia Software
---

### Post by Bloged on 2008-06-26
Hello all,

First I tried several other threads about the HDA ATI SB, but none of them seems to solve the problem I've got. The one who got it working in Xubuntu 7.10 was this one: [HDA ATI SB / INTEL Sound card problem [SOLUTION!]]("http://ph.ubuntuforums.com/showthread.php?t=616845") but this time to no availability.

After it worked in 7.10 I used it for about six months, after which it was time to upgrade to 8.04, so I ran the update manager. Everything went pretty smooth, after some troubleshooting all was running except sound. I never got round to posting this problem until now.

Ubuntu says everything is fine! But I got no sound from speakers or headphones!

Some output from different commands:
```
$ cat /proc/asound/card0/codec#* | grep Codec

Codec: Realtek ALC660-VD
Codec: Generic 1543 Si3054
```

```
$ lshw

	*-multimedia
                description: Audio device
                product: Radeon X1200 Series Audio Controller
                vendor: ATI Technologies Inc
                physical id: 5.2
                bus info: pci@0000:01:05.2
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=64 module=snd_hda_intel
```

```
$ aplay -l

card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ cat /proc/asound/cards

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfebf4000 irq 18
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfd7ec000 irq 20
```

```
$ cat /proc/asound/modules

 0 snd_hda_intel
 1 snd_hda_intel
```

```
$ cat /etc/modprobe.d/alsa-base

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

options snd-hda-intel model=3stack-660-digout
```

In Xubuntu 7.10 it worked with this option:
```
options snd-hda-intel model=auto
```
Now nothing seems to work!

Hopefully someone is able to help me getting sound from my laptop.

If you need more information about hardware just ask!

Thanks in advance,

Arjan Gelderblom

---

### Post by Bloged on 2008-06-26
Found something that is probably related in with dmesg:

```
$ dmesg
.....
[ 8637.837903] hda-intel: Invalid position buffer, using LPIB read method instead.
....

```

Edit: Problem seems to be gone when adding position_fix=1 in /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=3stack-660-digout position_fix=1
```

Thanks for any help,

Arjan Gelderblom

---


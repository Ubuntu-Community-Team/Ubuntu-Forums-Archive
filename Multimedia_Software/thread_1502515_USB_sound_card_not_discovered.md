---
title: "USB sound card not discovered"
date: 2010-06-05
forum: Multimedia Software
---

### Post by r0t on 2010-06-05
Here is yet another no sound thread... For some reason Pulseaudio seems not to discover one of my sound cards (card 1 below. Card 0 works fine, but card 1 does not turn up in the gnome-volume-control or elsewhere). I'm totally lost here, so any help would be very much appreciated.

I'm on Ubuntu 10.04.

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: M5461 [HDA ULI M5461], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: M5461 [HDA ULI M5461], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

$ cat /proc/asound/cards

 0 [M5461          ]: HDA-Intel - HDA ULI M5461
                      HDA ULI M5461 at 0xd9fd0000 irq 22
 1 [Device         ]: USB-Audio - USB Audio Device
                      Elite Silicon USB Audio Device at usb-0000:00:1c.1-1, full speed

```

```

$ cat /proc/asound/devices

  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio playback
  5: [ 1]   : control
  6: [ 0- 2]: digital audio capture
  7: [ 0- 1]: digital audio playback
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0- 0]: hardware dependent
 11: [ 0]   : control

```

```

$ cat /proc/asound/modules 
 0 snd_hda_intel
 1 snd_usb_audio

```

Not sure alsa-base.conf is supposed to look, something wrong there?
```

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```

```

leo@hallen:~$ cat /home/leo/.asoundrc.asoundconf
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Device
defaults.ctl.card Device
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device

```

---

### Post by r0t on 2010-06-05
...and this is gnome-volume-control, where I would expect two cards two show up:  [http://ubuntuone.com/p/6AP/](http://ubuntuone.com/p/6AP/)

---

### Post by lidex on 2010-06-05
How about these outputs:
```
lsusb
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by r0t on 2010-06-06
```

$lsusb

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0d24:0005  
Bus 003 Device 002: ID 18c3:6255  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard
Bus 002 Device 003: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```

$uname -a

Linux hallen 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

```

$cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.
```

```

$head -n 1 /proc/asound/card*/codec#*

Codec: Realtek ALC880
```

---

### Post by lidex on 2010-06-06
Try updating your alsa install via the link in my sig.

---

### Post by r0t on 2010-06-08
Thank you lidex! It turned out that it was ~/.asoundrc.asoundconf that caused all the problems. After removing that file everything works smoothly again!

---


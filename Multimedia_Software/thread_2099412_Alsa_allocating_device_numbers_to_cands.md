---
title: "Alsa: allocating device numbers to cands"
date: 2012-12-29
forum: Multimedia Software
---

### Post by Robbyx on 2012-12-29
I have 2 pci cards, a mother board built in sound card, and 2 usb sound devices. I am using Alsa rather than pulse.

As can be seen at the end I have tried to force the indexing via alsa-base.conf but that strategy is not working. The default sound is going to hda intel when I want it to go to c-media cm18768.

/proc/asound/cards:

```
 0 [CMI8768        ]: CMI8738-MC8 - C-Media CMI8768
                      C-Media CMI8768 at 0xd000, irq 20
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa000000 irq 46
 2 [Q9000          ]: USB-Audio - QuickCam Pro 9000
                      Logitech, Inc. QuickCam Pro 9000 at usb-0000:00:1a.7-3.4, high speed
 3 [Set            ]: USB-Audio - C-Media USB Headphone Set
                      C-Media USB Headphone Set at usb-0000:00:1a.7-3.1.2, full speed
``` 


/proc/asound/devices

```
  1:        : sequencer
  2: [ 0- 0]: raw midi
  3: [ 0- 2]: digital audio playback
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
  9: [ 1- 2]: digital audio capture
 10: [ 1- 1]: digital audio playback
 11: [ 1- 1]: digital audio capture
 12: [ 1- 0]: digital audio playback
 13: [ 1- 0]: digital audio capture
 14: [ 1- 2]: hardware dependent
 15: [ 1]   : control
 16: [ 2- 0]: digital audio capture
 17: [ 2]   : control
 18: [ 3- 0]: digital audio playback
 19: [ 3- 0]: digital audio capture
 20: [ 3]   : control
 33:        : timer
```


/etc/asound.conf
```

defaults.ctl.card 0
defaults.pcm.card 0
defaults.timer.card 0
```



aplay -l

```
robins@robins-EP35-DS3L:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Set [C-Media USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/etc/modprobe.d/alsa-base.conf 

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


# make stereo headphones on c-media cm 18768 go to 0
options snd-cmipci  index=0

# make logitech dual speakers on HDA intel
options snd-hda-intel index=1

# Make Ensoniq be default
options snd-ac97-codec index=4
```

Robin

---


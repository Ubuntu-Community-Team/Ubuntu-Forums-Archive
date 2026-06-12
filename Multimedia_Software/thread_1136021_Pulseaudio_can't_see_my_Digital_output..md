---
title: "Pulseaudio can't see my Digital output."
date: 2009-04-24
forum: Multimedia Software
---

### Post by kruykaze on 2009-04-24
I have my pc connected to my HT with a coax digital but Pulseaudio does not recognize alc1200 DIGITAL.But it does see alc1200 analog but no sound when I use it.Analog used to work under 8.10 but not since i got 9.04.
This is my setup
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by 3ps3s on 2009-05-09
I am having exactly the same problem.

```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```I have followed this tutorial to get *any* sound
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

PulseAudio lists only 1 sink:

```
:~$ pmcmd
>>> list-sinks
1 sink(s) available.
  * index: 0
    name: <alsa_output.pci_10de_7fc_sound_card_0_alsa_playback_0>
    driver: <modules/module-alsa-sink.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    state: SUSPENDED
    volume: 0: 100% 1: 100%
    muted: no
    current latency: 0.00 ms
    configured latency: 0.00 ms; range is 81.27 .. 81.27 ms
    max request: 14 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
    used by: 0
    linked by: 3
    module: 4
    properties:
device.api = "alsa"
device.class = "sound"
alsa.class = "generic"
alsa.subclass = "generic-mix"
alsa.name = "ALC1200 Analog"
alsa.id = "ALC1200 Analog"
alsa.subdevice = "0"
alsa.subdevice_name = "subdevice #0"
alsa.device = "0"
alsa.card = "0"
alsa.card_name = "HDA NVidia"
alsa.long_card_name = "HDA NVidia at 0xfeaf8000 irq 23"
device.description = "HDA NVidia - ALC1200 Analog"
device.string = "front:0"
device.buffering.buffer_size = "14336"
device.buffering.fragment_size = "1792"
device.access_mode = "mmap"

```

This is a 9.04 clean install. Has anybody figured this out yet?

Thanks.

---

### Post by jeremyjjbrown on 2009-05-09
Try this thread. It is has a lot of info for trouble shooting Pulse audio. 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Also, make sure the Ubuntu installer correctly identified your audio device via this thread.
[http://www.uluga.ubuntuforums.org/showthread.php?p=6430568](http://www.uluga.ubuntuforums.org/showthread.php?p=6430568)

---


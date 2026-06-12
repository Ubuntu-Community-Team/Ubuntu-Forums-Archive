---
title: "Playback open error: -2, no such file or directory"
date: 2011-10-30
forum: Multimedia Software
---

### Post by linuxnik18 on 2011-10-30
Al,

 Not getting any sound from my ATI R6xxHDMI driver.I have been looking around the forum for this exact problem and have not found out what it is. Possibly do i need to download the driver? Running 11.10

nikmotarx@Linuxnik18:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nikmotarx@Linuxnik18:~$ speaker-test -c 2 -r 48000 -D hw:1,3

speaker-test 1.0.24.2

Playback device is hw:1,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Playback open error: -2,No such file or directory
----------------------------------------------------------------------------

Card: HD-Audio Generic                               F1:  Help               &#9474;
&#9474; Chip: ATI R6xx HDMI                                  F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit          


----------------------------------------------------------------------------
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
    Subsystem: PC Partner Limited Device aa60
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fdefc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel





Thank you for all input,
Nik

---

### Post by BicyclerBoy on 2011-10-31
The only driver required could be the AMD catlyst video driver..
An AMD user will have to confirm..

The audio driver is snd-hda-intel

Why card1 you only have card0..

speaker-test -c 2 -r 48000 -D hw:0,3

dmesg | grep HDMI

ls -al /proc/asound/card0/eld#*

---

### Post by linuxnik18 on 2011-11-01
> **BicyclerBoy said:**
> The only driver required could be the AMD catlyst video driver..
An AMD user will have to confirm..

The audio driver is snd-hda-intel

Why card1 you only have card0..

speaker-test -c 2 -r 48000 -D hw:0,3

dmesg | grep HDMI

ls -al /proc/asound/card0/eld#*


Thank you for that input. Any AMD users?


Again thank you for all input,
Nik

---

### Post by BicyclerBoy on 2011-11-02
you can still try the other cmds offered ...

You can then likely answer the driver question yourself..

---


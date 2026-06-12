---
title: "old sound card requires oss not alsa"
date: 2017-08-03
forum: Multimedia Software
---

### Post by doru001 on 2017-08-03
My sound card works in OSS but not in ALSA. Is there any work-around to make it work in ALSA?
```
$ sudo lshw -C bus | head -n7
[sudo] password for user: 
  *-core                  
       description: Motherboard
       product: D865PERL
       vendor: Intel Corporation
       physical id: 0
       version: AAC27646-211
       serial: BTRL41208766
$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
       resources: irq:22 memory:fc000000-fcffffff
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_intel8x0 latency=0
       resources: irq:17 memory:fe100400-fe1005ff memory:fe100800-fe1008ff
```


When I first installed this board I was using Arch Linux and the sound worked for two minutes before it went silent and it remained silent. Replacing ALSA with OSS made it work flawlessly for many months. When I switched to Ubuntu I lost sound again, as Ubuntu has removed OSS support from its kernel ([https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)). Recently, after some update, I again enjoyed sound for a few minutes before it went silent. How is it even possible for ALSA to break a driver like this? 


The board is seen and the kernel modules are loaded: 
```
$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ lspci -v | grep -A7 -i "audio" 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Intel Corporation D865PERL mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at fe100400 (32-bit, non-prefetchable) [size=512]
    Memory at fe100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_intel8x0
    Kernel modules: snd_intel8x0
--
02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: LeadTek Research Inc. Winfast TV 2000XP Expert
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

$ lsmod | grep snd
snd_intel8x0           36864  2
snd_ac97_codec        106496  1 snd_intel8x0
ac97_bus               16384  1 snd_ac97_codec
snd_pcm                94208  2 snd_ac97_codec,snd_intel8x0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    69632  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
soundcore              16384  1 snd
```

---

### Post by doru001 on 2017-08-08
```
$ alsactl init 0
$ aplay /usr/share/sounds/alsa/Front_Center.wav
```
makes it work.

---


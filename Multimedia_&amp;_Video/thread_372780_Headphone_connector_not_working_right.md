---
title: "Headphone connector not working right"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by Goliash on 2007-02-28
I have Intel HDA soundcard on my laptop with chip ALC883. Soundcard works, module snd_hda_intel loads right. But when I plug in my headphones, sound is played but also from front speakers. I found out the headphone connector can be volumed in alsamixer the same as frontspeakers, so when I increase volume for front speakers, it is also applied for headphone. And when I try to change headphone volume, it does nothing.

 I tried to load module snd_hda_intel with various parameters, compiled the newest version of alsa, but it didn't help.
```
ALC883/888
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
          3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
          6stack-dig-demo  6-jack digital for Intel demo board
          acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
          medion        Medion Laptops
          targa-dig     Targa/MSI
          targa-2ch-dig Targs/MSI with 2-channel
          laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
          auto          auto-config reading BIOS (default)

```
It is notebook Fujitsu-Siemens AMILO Pro V3545.
Here is a part of lspci -v:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10d7
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)
```
And aplay -l list:
```
Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
```

---

### Post by Maxtorm on 2007-02-28
Have you tried using alsamixer to turn Phone Sense on/off?

---

### Post by Goliash on 2007-03-01
There is a no such possibility in alsamixer, just Headphone, PCM, Front bars, two mic bars (Front, Mic), Caller ID and Off-hook switches, two Input source switches.

I think I need to tell to soundcard driver that this connector is not Front, but Headphones.

---

### Post by Maxtorm on 2007-03-01
That's odd.  I had an almost identical problem with an Intel board in a Compaq desktop (D530) and it ended up being the Phone Jack Sense switch.  Given the level of expertise evident in your original post, I'm sure you already know this, but in alsamixer there are three different modes of display.  I think they're "Playback" (F3), "Capture" (F4) and "All" (F5).  Were you in "All" mode when poking around for the Phone Jack Sense switch?  Just seems like the list of inputs/sources/outputs you have is short for that sound card.

---

### Post by Goliash on 2007-03-03
I have no Phone Jack Sense switch in alsamixer. But I figured out that I was wrong when I loaded and unloaded module snd_hda_intel only with ```
sudo modprobe -r snd_hda_intel
sudo modprobe snd_hda_intel model=xyz
``` because I forgot restart alsa service. So I tried to reboot all computer after every change of module parameter and mostly it didn't work. Either front speakers and headphones played sound together or no sound was played. After about six reboots I tried ```
sudo sudo modprobe snd_hda_intel model=acer
``` and both out lines (front speakers and headphone connector) worked and in alsamixer I can volume each separately: front speakers by surround bar and headphone connector by front bar. So when I want to listen music only in headphones I must mute surround output. Phone Jack sense doesn't work.

---


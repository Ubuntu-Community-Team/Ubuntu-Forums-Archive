---
title: "Sound card rec. by Alsa but not displaying in aplay"
date: 2013-02-19
forum: Multimedia Software
---

### Post by keegs1 on 2013-02-19
Hi guys, I've been having a bit of trouble getting my sound card (Asus Sonar DGX) to work with alsa, I have already run through the troubleshooting guide twice and looked at numerous other threads but to no avail..The card appears to be seen by the system and alsa is saying that it is recognising it and activating it :
```
Sound cards recognized by the system:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
03:04.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]
Sound cards recognized by ALSA:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
03:04.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]
Sound cards recognized by ALSA, and activated:
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
03:04.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]

```
and running lspci -v | grep -A7 -i "audio" shows that the system is also picking up that the card is installed: 
```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f7300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

--
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 83f4
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

--
03:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
        Subsystem: ASUSTeK Computer Inc. Device 8521
        Flags: medium devsel, IRQ 11
        I/O ports at d000 [disabled] [size=256]
        Capabilities: <access denied>

```
However, it is not showing up in aplay -l, /proc/asound/cards or /proc/asound/devices ..

```
keegs@Media-Server:~$ sudo aplay -l
[sudo] password for keegs:
**** List of PLAYBACK Hardware Devices ****
Home directory /home/keegs not ours.
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

 Could it be because alsa is not loading a kernel driver for the sound card, and if so how can I fix this? It should be loading the oxygen-hd driver for it which I have on my system..Please any help would be appreciated!

---

### Post by keegs1 on 2013-02-19
Reading further, my card is supported by Alsa 1.0.26, however I am only running 1.0.25 on Ubuntu 12.04, is there anyway to update to 1.0.26?

---


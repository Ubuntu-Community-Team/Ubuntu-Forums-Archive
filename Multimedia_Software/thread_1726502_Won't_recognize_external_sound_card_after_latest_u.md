---
title: "Won't recognize external sound card after latest update"
date: 2011-04-11
forum: Multimedia Software
---

### Post by begtognen on 2011-04-11
I'm running Ubuntu 10.04.

Until yesterday, my Audiophile sound card was working beautifully. I ran the latest update, and now it doesn't show up under Sound Preferences. (When I plugged in a USB headset, that appeared under Sound Preferences and worked just fine.)

The sound card IS listed under aplay -l.

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audiophile192 [M Audio Audiophile192], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audiophile192 [M Audio Audiophile192], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The sound card IS listed under lspci | grep -i audio, as Envy24 (I'm not sure why it's called Envy24 here instead of Audiophile, but that's always been the case.)

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

```

Here's the Alsa information: [http://www.alsa-project.org/db/?f=16c8ed6d93df20faa65d5d19ac89af8d64ea4b53]("http://www.alsa-project.org/db/?f=16c8ed6d93df20faa65d5d19ac89af8d64ea4b53")

The sound card is listed as:

```
!!Soundcards recognised by ALSA
!!-----------------------------

0 [Audiophile192  ]: ICE1724 - M Audio Audiophile192   
                     M Audio Audiophile192 at 0xdf00, irq 2
```

If I run Alsamixer from the terminal, the correct Audiophile sound card is the one shown.

I'm not sure what to do next. Thanks very much for any help/suggestions.

---

### Post by begtognen on 2011-04-19
I updated to 10.10, and the sound card is working beautifully now.

---


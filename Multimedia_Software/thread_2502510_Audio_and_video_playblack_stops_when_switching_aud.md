---
title: "Audio and video playblack stops when switching audio output to HDMI/DP"
date: 2024-11-18
forum: Multimedia Software
---

### Post by twistered2 on 2024-11-18
I am running 22.04.5 version on my old HP EliteBook 800 G1 TWR and as   mentioned in the title - sound and video stops when I change audio   output to HDMI/DP (box has two display ports, both behave the same way   and there is no HDMI port). Monitor displays video correctly via DP, but   sound needs to be played via internal speaker - then i can watch   movies. If only I switch audio to HDMI/DP movie playback stops (eg. in   web browser) - video is still there and monitor shows everything else   correctly. Here is the output of **inxi -GA** command. Thanks in advance for any tips on findings root cause if this issue.
```
Graphics:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics
    driver: i915 v: kernel
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.9 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1200~60Hz
  OpenGL: renderer: Mesa Intel HD Graphics 4600 (HSW GT2)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    driver: snd_hda_intel
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.8.0-48-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```

---


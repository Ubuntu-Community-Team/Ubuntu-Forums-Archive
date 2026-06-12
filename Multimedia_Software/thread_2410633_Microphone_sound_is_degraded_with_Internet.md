---
title: "Microphone sound is degraded with Internet"
date: 2019-01-18
forum: Multimedia Software
---

### Post by bicounet18 on 2019-01-18
Hello,
With a Lenovo ideapad 330-17AST0 laptop in dual-boot Win10 and Xubuntu 18.04.1.
The internal microphone of the laptop works well with Audacity .. The Audio output works properly.
But, on the Internet (messenger, micro test with [https://online-voice-recorder.com/en/](https://online-voice-recorder.com/en/))
the microphone comes out only crackling.
Browser tested: Firefox, chromium.
**lspci | grep [Aa]udio**
```
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15b3
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Device 157a
```
[B]cat /proc/asound/card0/codec* | grep Codec
[/B]```
Codec: Realtek Generic
```[B]
cat /proc/asound/version[/B]
```
Advanced Linux Sound Architecture Driver Version k4.15.0-43-generic.
```
[B]cat /proc/asound/cards
[/B]```
0 [Generic        ]: HDA-Intel - HD-Audio Generic                       HD-Audio Generic at 0xf0d64000 irq 40
1 [HDMI           ]: HDA-Intel - HDA ATI HDMI  HDA ATI HDMI at 0xf0d60000 irq 39
```
**[B]cat /proc/asound/pcm**[/B]
```
00-00: Generic Analog : Generic Analog : playback 1 : capture 1
01-03: HDMI 0 : HDMI 0 : playback 1
```[B]
[B]cat /proc/asound/modules
[/B][/B]```
0 snd_hda_intel
1 snd_hda_intel
```

Thanks for your help

---


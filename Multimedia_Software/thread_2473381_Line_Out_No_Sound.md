---
title: "Line Out No Sound"
date: 2022-04-02
forum: Multimedia Software
---

### Post by gus_zernial on 2022-04-02
I have an ASrock X570M Pro4 AMD MicroATX motherboard, which has a Realtek ALCS 1200A audio chip. Pavucontrol detects the audio chip as a "Starship/Matisse HD Audio Controller Analog Stereo" device, which is confusing, but in any case it uses Intel sound drivers:

lspci -k | grep -A 4 Audio
0d:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller
        Subsystem: ASRock Incorporation Starship/Matisse HD Audio Controller
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

There's also a Radeon RX6500 XT graphics card on the system, which can provide HDMI audio out, but my speaker system doesn't take HDMI sound in, do I've muted that sound device. 

All the volume sliders are turned up in AlsaMixer. The PavuControl sound bar shows sound output, but I get no sound thru the green motherboard audio out jack to the speakers, except possibly a faint scratchy noise. 

Ideas to diagnose and/or fix appreciated.

---

### Post by Autodave on 2022-04-07
When you click on the sound icon, look at the first or top line and make sure that it is set correctly.......I just went through the same thing last night.

---


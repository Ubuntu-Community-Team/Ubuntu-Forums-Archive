---
title: "Surround Sound HDMI distorted/strange"
date: 2018-03-12
forum: Multimedia Software
---

### Post by galliano16 on 2018-03-12
Hi guys, I hope somebody here can help me to solve my issue...

Few days ago I connected my HTPC to a receiver via HDMI and intended to enjoy the 5.1 Surround Sound. And the frustration came up.

The 5.1. sound is distorted, I don't know how to really describe, it seems to me it is not played at the correct sampling rate. On the other end, if I select in Pulseaudio HDMI stereo output, the sound is OK, but often chopped and when I want to check the speakers I first need to click 2 or 3 times the speaker right or speaker left button before the sounds comes. Does anybody know what the problem could be and how to solve it?

Here some hopefully useful information: 

I already did: ```
sudo apt-get install libasound2-plugins-extra
```

Output of ```
cat /proc/asound/cards  

0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 19
```

Output of ```
sudo apt-get install inxi && inxi -Fz

System:    Host: htpc Kernel: 4.10.0-42-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: GA-MA785GMT-UD2H
           Bios: Award v: F10b date: 07/13/2010
CPU:       Dual core AMD Athlon II X2 250 (-MCP-) cache: 2048 KB 
           clock speeds: max: 3000 MHz 1: 2300 MHz 2: 1800 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS880 [Radeon HD 4200]
           Display Server: X.Org 1.19.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD RS880 (DRM 2.49.0 / 4.10.0-42-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.7
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp3s0 state: down mac: <filter>
           Card-2: Realtek RTL8191SU 802.11n WLAN Adapter driver: r8712u
           IF: wlx00116b485de3 state: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (50.4% used)
           ID-1: /dev/sda model: ST3500418AS size: 500.1GB
Partition: ID-1: / size: 29G used: 6.0G (23%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 425G used: 224G (56%) fs: ext4 dev: /dev/sda5
           ID-3: swap-1 size: 6.14GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 24.9C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 204 Uptime: 5 min Memory: 1055.7/5458.1MB
           Client: Shell (bash) inxi: 2.2.35 
```
Output of ```
pactl list sinks short

1    alsa_output.pci-0000_00_14.2.iec958-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
2    alsa_output.pci-0000_01_05.1.hdmi-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
```

I would hate to go back to Windows for the sound problem and really hope to get the thing working.

My ubuntu version is the 16.04 LTS

---


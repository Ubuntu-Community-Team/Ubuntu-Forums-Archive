---
title: "Volume controls don't work (panel icon and laptop's keys)"
date: 2015-06-22
forum: Multimedia Software
---

### Post by dowoshek on 2015-06-22
Hello,
Lubuntu 14.04. There's sound and I can control volume for example in youtube but I can't control it on the panel (it's grey all the time). Alsamixer can't control Master volume, only PCM. And my laptop's volume control keys also don't work (it works at WinXP).

lspci
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by Bucky Ball on 2015-06-22
*Thread moved to **Multimedia**.*

Not related to desktop environment problems. 

Let's have a closer look:

```
sudo lshw -C sound
```

Post the output here, thanks. 

Also, is your audio device showing up in Pulse Audio Volume Control? If PAVControl is not installed, install it and have a look. Hit the 'Configuration' tab and see what device is set up as the Primary device there.

---

### Post by dowoshek on 2015-06-22
sudo lshw -C sound
```
  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=64
       resources: irq:40 memory:febf8000-febfbfff
```

I'd like to solve it without installing pulseaudio. This is old laptop with small performance issues even when browsing, so the less the better. However, after installing pavucontrol/pulse it solves the problem with icon but still can't use laptop keys. But can I solve it without pulse? (it was the reason to post it at Desktop environments because I see this as LXDE problem)

---

### Post by Bucky Ball on 2015-06-22
Erm, you Pulse is probably already installed by default in Lubuntu. Correct me if I'm wrong ...

---

### Post by dowoshek on 2015-06-22
No, it comes with Xubuntu but not Lubuntu.

---

### Post by Rex Bouwense on 2015-06-22
Alsamixer is the default install for Lubuntu.

---

### Post by Bucky Ball on 2015-06-23
I checked it out myself, thanks. Good to know. Learn something everyday.

---


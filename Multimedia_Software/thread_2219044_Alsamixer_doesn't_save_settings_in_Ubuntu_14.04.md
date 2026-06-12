---
title: "Alsamixer doesn't save settings in Ubuntu 14.04"
date: 2014-04-22
forum: Multimedia Software
---

### Post by Cvetan on 2014-04-22
When i set levels in alsamixer and exit, the settings are reseted at next login.
The master volume stays on the set level, but my subwoofer is reseted at 100.

In every Ubuntu version till now this was enough to save settings. Has something changed, and do i have to do something to save settings?

[B]edit:
[/B]Something is definitely wrong. I set the output to 5.1 in sound settings (gui via indicator) and i have surround output until i logout. When i logout, i don't have surroung anymore. Than i select stereo output, then the subwoofer is loud. I retrieve to 5.1 output, and again i have surround until i logut. The levels at alsamixer seem to be preserver when 5.1 i selected in sound settings, but they don't influence anything since i don't have surround.
```
lspci
```
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation B75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)


```

---

### Post by Cvetan on 2014-08-07
I discovered that
```
alsactl restore
``` is not executed at startup. If i manualy run it, the levels i have set are restored. The only remain question is how to make system run it, besides that i put it into startup script. 

Only to mention that this is still actual, even in Ubuntu 14.04.1. I was hoping some update will fix it, but no. :(

---

### Post by Yellow Pasque on 2014-08-07
Pulseaudio is infamous for clobbering the alsamixer settings. I don't know any way to make it respect those settings.

---

### Post by Cvetan on 2014-08-08
For now i solve this with startup script in my user acount. I put:
```
amixer set LFE level
```
in it. I hope some update will resolve this. For now it works like this.

---


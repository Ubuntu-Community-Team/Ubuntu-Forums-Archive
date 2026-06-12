---
title: "Microphone not working in some apps"
date: 2020-04-16
forum: Multimedia Software
---

### Post by pgslmatias on 2020-04-16
My physical hardware itself is fine, and when I'm on a Zoom call people can hear me. However when I'm using any other video conference app, such as Google Hangouts, Discord and even video calls using Facebook Messenger it doesn't work (there were some times when it briefly, for some seconds, worked in Discord app). I'm not sure how to debug it because everything I find is for when your microphone doesn't work at all, but that is not the case. I'm not sure what causes the microphone to malfunction only in some apps (that is, every app apart from Zoom).

This my **lsb_release -a**:
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

This is **lspci**
```
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Device 3e9b
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 SATA controller: Intel Corporation Device a353 (rev 10)
00:1d.0 PCI bridge: Intel Corporation Device a337 (rev f0)
00:1e.0 Communication controller: Intel Corporation Device a328 (rev 10)
00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)
02:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)

```

This is [B]lspci -v | grep -A7 -i "audio"
[/B]
```

    00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1219
    Flags: bus master, fast devsel, latency 32, IRQ 127
    Memory at a4310000 (64-bit, non-prefetchable) [size=16K]
    Memory at a4100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+

```

This is **aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My laptop is a  MSI MS-16P6.

What should I do? I thought this could be a driver issue, but I'm not sure. One thing that might help is that the applications detect my microphone, they just don't detect any sound, but I'm sure the microphone is functioning because in Zoom there is no problem.

---

### Post by Autodave on 2020-04-16
Have you gone into the sound settings and made sure that the mic's volume was turned up?  I have had that problem when switching programs: the volume will be up on one, but then the whole way down on the next one.

---


---
title: "Intel 82801BA-ICH2 - External speakers not detected"
date: 2009-03-03
forum: Multimedia Software
---

### Post by barraclou on 2009-03-03
I know that I am probably not creative in my thread topic, but I just installed Ubuntu 8.10. My sound card and my external speakers are working, but that tiny internal speaker won't quit playing loud while I use the external speakers or not. I reviewed the Comprehensive Sound Problem Solutions Guide sticky post, but I am still stuck with my bug. I probably need to configurate something but I am not sure where exactly. 

Your help is appreciated, thanks in advance.

```
me@me-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
Subdevices: 1/1
Subdevice #0: subdevice #0
me@me-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 01)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
me@me-desktop:~$ 

```

---


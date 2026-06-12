---
title: "Intel 815 Chipset Sound Nightmares!"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by MikeJ112 on 2007-06-04
Hi, I have aquired an old PC which I have upgraded and am now running Ubuntu 7.04. I am having problems installing the soundcard drivers. The PC has a Asus mobo, lspci shows the soundcard;

```
mike@desktop-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 02)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
mike@desktop-ubuntu:~$ 
```

when i type sudo modprobe snd-intel8x0 , which is the driver I need to install, and enter my password, it does nothing.

aplay-l shows;
```

mike@desktop-ubuntu:~$ aplay -l
aplay: device_list:222: no soundcards found...
```

Any help will be much appreciated!!

Mike

---


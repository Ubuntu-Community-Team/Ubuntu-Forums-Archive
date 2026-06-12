---
title: "problem getting webcam to work in ubuntu 8.10"
date: 2009-03-11
forum: Multimedia Software
---

### Post by rajveer9 on 2009-03-11
Hi am new to ubuntu and am having problem getting my webcam to work. It's a Kinamax WCM-6LNV Web Cam (Kinamax - PC - 640 x 480 ). I search a lot and tried everything but couldnt make it work. 

Some info which might be useful:
1.lsusb give me the following:-
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 06a2:0003 Topro Technology, Inc. 
Bus 003 Device 002: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) ADSL LAN Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

2. ls -la /dev/video0 gives me an error msg even if i run the command as root:-
ls: cannot access /dev/video0: No such file or directory

Some help would be greatly appreciated. Please tell me the detail steps. Thanks in advance

---

### Post by shamimkhaliq on 2009-03-11
i've been searching and there are a lot of wecams that don't work in linux. my logitech fusion webcam too (i tried all the workarounds i found in forums).

i'm thinking of buying a new webcam. Here is a list of webcams and where to find their drivers: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

ignore that, my webcam is on the list of supported uvc devices, but there are loads of threads on the net about it not working.

---

### Post by Berduchwal on 2009-05-16
see kernel patch: [http://patchwork.kernel.org/patch/16936/](http://patchwork.kernel.org/patch/16936/)

---


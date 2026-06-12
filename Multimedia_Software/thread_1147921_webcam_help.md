---
title: "webcam help"
date: 2009-05-03
forum: Multimedia Software
---

### Post by vkeifreek on 2009-05-03
Ok I'm a newbie at linux in general. Well I hooked up my webcam (Gigaware not to sure of the model number sadly) and well it's not working I was wanting to see if anyone could help me out with this I'm using kubuntu intrepid.

---

### Post by cariboo on 2009-05-04
Could you open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

This will help us find what driver your webcam needs, paste the output in your next post.

---

### Post by vkeifreek on 2009-05-04
chris@chris-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye WebCam
Bus 003 Device 002: ID 062a:0003 Creative Labs
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-desktop:~$

---

### Post by vkeifreek on 2009-05-05
someone help

---

### Post by vkeifreek on 2009-05-05
please I've tried to look it up and got nowhere.

---

### Post by xc3RnbFO8P on 2009-05-05
Do you have 2 webcams connected?

---

### Post by vkeifreek on 2009-05-05
no only things plugged in to my usb ports is my mouse and my webcam

---

### Post by xc3RnbFO8P on 2009-05-05
I dont know if they hafe fix this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267522]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267522")

---


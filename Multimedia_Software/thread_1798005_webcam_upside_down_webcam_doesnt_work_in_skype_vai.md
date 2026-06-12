---
title: "webcam upside down webcam doesnt work in skype vaio"
date: 2011-07-05
forum: Multimedia Software
---

### Post by teacupey on 2011-07-05
i have sony viao vgn-fz11 Can someone please help ,im new user to ubuntu been trying to get webcam working properly at the moment its upside down and does not work in skype at all just get black screen does this look correct    ? do i have the right driver?i will try and give as much information as i can   

~$ lsmod | grep videodev
videodev               75143  3 uvcvideo,meye,v4l2_common

$ lsusb
Bus 007 Device 002: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


any help would be greatly appreciated thanks

---

### Post by siabost on 2011-09-04
Have a look at the third post here [http://ubuntuforums.org/showthread.php?t=1744189](http://ubuntuforums.org/showthread.php?t=1744189)

On one VAIO laptop this worked perfectly for me but on another I still getan upside-down webcam picture. So, not guaranteed to work but might be worth a try.

Good Luck

---

### Post by ronniew on 2011-12-13
Turn the laptop upside down.... wala fixed!

---


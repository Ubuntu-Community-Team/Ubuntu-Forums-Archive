---
title: "Mobile boradband installation"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by wacbiarf on 2012-09-08
Hi
 i am a new user of Ubuntu. on my own computer, i use ubuntu 12.04 but because of old cpu, i installed 10.04LTS on my uncle's laptop. 
The problem is about the mobile modem, Huawei k3770 (Vodafone).
When i plus it to my pc, it only asks for pin code and connects happily.
But on laptop, i tried to just create a connection which didn't work.
I tried

```

lsusb
...
sudo apt-get install usb_modeswitch

```

and it says i couldn't find the usb_modeswitch.conf pack.
i installed modeswitch packs from application manager and i found an usb_modeswitch.conf file, copied it to /etc . 
But the problem still continues. What can i do now?

---


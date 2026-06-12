---
title: "[xubuntu] Wifi not working on Dell Latitude D430 running xubuntu 13.04"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by maurice3 on 2013-08-11
[COLOR=#000000]I just installed Xubuntu 13.04 on my Dell Latitude D430. It is not detecting my [/COLOR][COLOR=#000000][COLOR=#000000]Broadcom BCM4311 wireless chipset which also didnt work with ubuntu 12.10 or 13.04. Can someone help me please, I am very new to xubuntu but have experience with the terminal. 
Also, theres a fix for ubuntu 12.10 but when I tried it didnt work:

[/COLOR][/COLOR][COLOR=#000000]http://ubuntuforums.org/showthread.php?t=2072887[/COLOR]

---

### Post by chili555 on 2013-08-11
Please get a temporary ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Detach the ethernet. Is it working now?

---

### Post by maurice3 on 2013-08-11
> **chili555 said:**
> Please get a temporary ethernet connection, open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Detach the ethernet. Is it working now?

I connect it to my wireless g linksys usb network adapter and the wifi worked, but I need this computer for work and I cant set that up everytime. I tried your command, but when I entered:

```
sudo apt-get remove --purge bcmwl-kernel-source
```

It said:
```
Invalid operation bcmwl-kernel-source
```

---

### Post by chili555 on 2013-08-11
Maybe we can't remove bcmwl-kernel-source because it isn't installed at all; check:```
sudo dpkg -s bcmwl-kernel-source
```If it says it isn't installed, you may safely skip that step.> the wifi worked, but I need this computer for work and I cant set that up everytime. I don't understand that, exactly. We are trying to get your wireless to work anywhere on any network without having to set up anything else...ever.

---


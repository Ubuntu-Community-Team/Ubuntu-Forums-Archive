---
title: "How do I get wireless to automatically start?"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by dot-borg on 2011-06-16
Hi, I just got a new Lenovo V570 and installed the latest Ubuntu on it. When Ubuntu starts up, I can see that it's killing the radio. Once the desktop is up then I re-enable the radio but I get the message "Wireless Network Disconnected - you are now offline". I can disable the radio (no message) and then re-enable again and get the same message.

I know the drivers work because I can manually start wireless like this:
```
sudo ifconfig wlan0 up
sudo wpa_supplicant -Dwext -iwlan0 -c'/path/to/config/file' &
sudo dhclient wlan0
```
Anyone have an idea about how I can get wireless networking to automatically start when I boot?

[edit]
I figured it out. The problem was the acer_wmi kernel module.

---


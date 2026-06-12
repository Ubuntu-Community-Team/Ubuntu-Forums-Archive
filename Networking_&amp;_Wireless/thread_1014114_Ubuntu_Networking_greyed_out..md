---
title: "Ubuntu Networking greyed out."
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by The-Kernel on 2008-12-17
Hi, I have Ubuntu 8.10 installed on my laptop. For some reason when I left click on the Networking icon in the panel, all the options are grayed out. How do I change it so that I can use the Ubuntu Network manager.

Also, I can connect to any unprotected network, however, if there is WPA or WEP, I cannot connect to the the wireless using ifconfig/iwconfig or wi-fi radar. It just won't grab the IP for some reason. What's a good app for this?

Here's my system info:

Wireless Broadcom BCM4318 Airforce one 54g
Intel Pro/100 VE Ethernet

---

### Post by S_e_P_p on 2008-12-18
Hello,

Do you use the restricted Broadcom Driver? 

You should if not use it. If your wlan isn't working use a wired connection. Install all updated. Retart and you should see under System -> Hardware the restricted Broadcom WLAN driver.

Afterwards:

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

and then activation through this (if you have an acer):
echo 1 > /sys/devices/platform/acer-wmi/wireless

Greets
SePp

---


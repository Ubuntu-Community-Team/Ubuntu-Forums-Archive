---
title: "USB Adapter to WIFI Thomson TG122n ! HELP!"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by danio482 on 2011-03-20
Hello !

I'm from Poland and i have a wifi in my home . To the connecting i'm using an USB Adapter Thomson TG122n . Does it posibble to install this Adapter on Ubuntu 10.10 ?!

This is my result of " sudo lsusb " command :

[[IMG]http://img38.imageshack.us/img38/7708/zrzutekranumm.png[/IMG]](http://img38.imageshack.us/i/zrzutekranumm.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by flash63 on 2011-03-20
Hello,
try this:
```
echo 'install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb; /bin/echo "0bda 8174" > /sys/bus/usb/drivers/rtl819xU/new_id' | sudo tee /etc/modprobe.d/r8192s_usb.conf
```
Copy the Firmware:
```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/ 
```
Test it
```
sudo modprobe r8192s_usb
iwconfig
```
If the solution works ...
```
sudo gedit /etc/udev/rules.d/10-wlan_stick.rules 
```
Content:
```
# UDEV-Rule for Thomson TG122n 0bda:8174
SUBSYSTEM=="usb", ATTR{idVendor}=="0bda", ATTR{idProduct}=="8174", RUN+="/sbin/modprobe r8192s_usb"
```
After Restart the stick should work automatically.

---

### Post by danio482 on 2011-03-20
Dude ! you're big man xD Thankssss :) On Poland ubuntu support forum  i'm waiting for 2 days without help :)

---


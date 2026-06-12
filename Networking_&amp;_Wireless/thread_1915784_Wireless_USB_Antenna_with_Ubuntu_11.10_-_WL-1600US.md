---
title: "Wireless USB Antenna with Ubuntu 11.10 - WL-1600USB"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by tonqua on 2012-01-26
Hi,
got ubuntu 11.10 on a new box, trying to get to work a "high power wireless 11g usb dongle" Air Live WL-1600USB.
No luck so far,
I checked the [[SIZE=1]Wireless network troubleshooter[/SIZE]]("https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html"). The only positive I get is that *sudo lsusb* gives me* Bus 002 Device 003: ID 1b75:8189 Ovislink Corp. *which seems to be the device.
No drivers, no luck with ndiswrapper,
any idea?
Thanks.

---

### Post by chili555 on 2012-01-27
Please check here: [http://ubuntuforums.org/showthread.php?t=1904757&page=5](http://ubuntuforums.org/showthread.php?t=1904757&page=5)

Start at post #41. Since you haven't installed compat-wireless, skip those steps.> ```
gedit /etc/udev/rules.d/network_drivers.rules

```
Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1b75", ATTR{idProduct}=="8189", RUN+="/sbin/modprobe -qba rtl8187"
```

Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```

Add one long single line:
```
install rtl8187 /sbin/modprobe --ignore-install rtl8187 $CMDLINE_OPTS; /bin/echo "1b75 8189" > /sys/bus/usb/drivers/rtl8187/new_id

```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:
```
sudo modprobe rtl8187
```Post back if you get stuck.

---

### Post by tonqua on 2012-01-29
Thank you very much,
I'm not quite sure what I did but it works.
Thanks!

---


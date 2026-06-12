---
title: "Help pls: trouble getting ralink usb wireless working"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by lblythen on 2011-07-19
Can't get my new TP-Link TL-WN321G USB wireless dongle working on Kubuntu 10.04, stock kernel 2.6.32-33. Works fine with Windows 7.  Internet connection is fine on the same Ubuntu box when I use an Ethernet cable instead of the dongle. The USB port's working and the Device Notifier in my system tray reports when I plug a different  type of dongle into it, but it doesn't report anything when I  plug in the WN321G. Don't know if that matters, because plugging it in causes ifconfig to report wlan0 and unplugging causes wlan0 to disappear; also lsusb correctly reports the device when it's plugged in. LED flashes rapidly when plugged in then settles to occasional regular, brief flash. Chipset is RAlink's RT73 and I have the latest rt73-common package installed. Can't get the companion firmware-ralink though - doesn't exist in Ubuntu? rt73.bin is in /etc/firmware but I noticed there was no firmware.conf in there so presumably update_firmware can't know what to do with rt73.bin     lsmod reports rt2800usb, rt2x00usb and rt2x00lib. Not certain these are the correct modules for the rt73 chipset. Any help much appreciated - TIA.

---


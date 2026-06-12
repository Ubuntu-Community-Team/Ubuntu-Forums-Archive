---
title: "Bluetooth search doesn't find any device"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by tecoholic on 2011-11-01
I have a Lenovo S10-3c netbook. I installed Ubuntu 11.10. Everything works flawlessly, except the bluetooth. I tried the network manager to add my phone, but the searching goes on for ever an does not find the device.

I run ```
hcitool dev
``` and ```
lsusb
``` and it shows a bluetooth device **Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**, but when I use ```
hcitool scan
``` it shows ```
scanning...
``` but nothing turns up. I have tried restarting bluetooth using ```
sudo service bluetooth restart
```. It reports stopping and starting the service but still doesn't find the device.

I have gone through a number of threads, but couldn't find solution.
How to make it find devices. Kindly help.

---

### Post by j_kamath on 2011-12-03
Techolic: Which location are you from? India I presume since the L S10-3c is only available here.

---


---
title: "D-Link DWL-G650 AirPlus XtremeG NOT DETECTED!"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by audax321 on 2006-01-16
Okay, I have two of these (one is brand new). The older one is version B4 and worked on Hoary pretty much plug and play. The new one is B5 and I haven't used it before. The problem is that neither is being detected by Breezy. There is NO dmesg output although the card is getting power from the laptop (the lights are blinking). Also iwconfig does not list the card. I have no idea what is going on and searches have not helped. Any ideas? Both cards installed perfectly fine in Windows...

---

### Post by Lambert on 2006-01-16
run the command lspci -v. Is it an atheros chipset in the device? I believe it is as I have a B5 card.

If it is atheros then make sure you have linux-restricted-modules for the kernel you're running installed. You can do that with this command.

sudo dpkg -s linux-restricted-modules-`uname -r`

Look for this line.
Status: install ok installed
or
Package `xxx' is not installed and no info is available.


If not you need to install this package to get the driver. It's on the install cd so you don't need internet access to get it.

---


---
title: "Fresh Install, Neither Network Device Detected"
date: 2005-01-09
forum: Networking &amp; Wireless
---

### Post by talkingwires on 2005-01-09
The other day I did a new install an older Dell laptop. During the installation, Ubuntu recognized my two PCMCIA network devices, a Netgear FA410TX and a Netgear MA401 (Prism-based wireless). After the install had finished, both devices were missing from networking configuration applet and the wireless connection applet said there were no wireless devices installed.

All the proper modules seem to be loaded (pcmcia, prism45, etc). Running iwconfig turns up my wireless card (listed a eth1 instead of wlan0) but not my other card. Adding the devices in the network configuration applet doesn't seem to change anything and etc/networks/devices remains empty. Any ideas?

---

### Post by randy on 2005-01-10
The wireless connection applet doesn't work until I've brought the device up.  Try executing sudo ifup eth1 or sudo ifup eth0 to bring up your network devices.

---

### Post by talkingwires on 2005-01-10
Yes, I've got them recognized now.

Unfortuantely, DHCP refuses to work with my wireless card, attempts to set the channel result in cryptic messages about the operation not being supported or SIOCSIFFLAGS timing out, and manually plugging in the IP address does nothing. On top of all this, the system just started freezing occcasionally when loading the hotplug module and often when starting ACPI. Booting into Windows (to get on the Internet) finds that all the hard resetting I've been doing when the system locks irrecoverably has apparently created some bad blocks on my harddrive. :sad:

---


---
title: "Link-local addressing not working over USB connection"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by kyldere on 2013-05-20
I am having issues getting an auto-ip address to be assigned to a USB-ethernet connection when there is no DHCP server available. The device in question is running 12.04.1, and I have avahi-autipd installed. It is connected to another device that acts as a bridge to the main part of the network, and I need to have a static IP assigned to the USB connection as well (alias USB0:0). When the bridge is connected, the USB connection will come up and the USB root (USB0) will get a dynamic IP that is in the correct range, but if I disconnect the network cable from the bridge and reboot the system, the USB will not get a link-local address (169.254.xxx.xxx), and consequently, the static IP will not get assigned to the alias.

I have tried out the scenario with the onboard NIC (eth0), and using the same settings in /etc/network/interfaces (changing usb0 to eth0) seem to enable link-local to work correctly. I cannot use eht0 to communicate with the bridge; it has to use the USB connection. Anyone have any ideas as to what I am doing wrong? Thanks!

---

### Post by kyldere on 2013-06-19
So, for anyone that has this problem, I finally figured it out. I ended up making sure that the avahi-autiopd package was loaded and the profile for the USB connection in /etc/network/interfaces was set to dhcp (ipv4ll seemed to only supply a link-local address). I edited the /etc/dhcp/dhclient.conf to use the timeout (set to 30 seconds) and the retry (set to 60 seconds) statements. This will allow the USB connection to obtain a link-local address (169.254.xxx.xxx) and subsequently, the static IP defined in the alias.

---


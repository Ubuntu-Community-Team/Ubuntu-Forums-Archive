---
title: "Bluetooth tether from laptop to desktop, both Ubuntu Maverick"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by fredarneto on 2011-03-16
Hi,

I've got an Ubuntu Maverick desktop/server with an internet connection and Bluetooth support. I've also got an Ubuntu Maverick laptop also with Bluetooth support. They can l2ping each other over bluetooth.

From my laptop, l2ping the desktop/server:
root@fredlaptop:~# l2ping server
Ping: server from laptop (data size 44) ...
44 bytes from server id 0 time 18.81ms
44 bytes from server id 1 time 19.75ms
44 bytes from server id 2 time 43.81ms
44 bytes from server id 3 time 37.80ms
Send failed: Connection reset by peer

I have no other way of connecting the laptop to the desktop. No wifi, no ethernet, nothing. Only Bluetooth.  I want to setup my desktop to be the Bluetooth PAN server. I want to figure out how to configure the desktop and laptop so that they auto-connect everytime. I also need this to work automatically without requesting the PIN to be entered every time. I've tried editing the /etc/bluetooth/network.conf and following the various howtos but they seem out of date (no more pand, no more /etc/bluetooth/default or /etc/init.d/bluetooth) since Maverick uses bluez4. I also want to setup my desktop to have its DHCP server assign an IP address automatically to the laptop when the laptop connects. Anyone figured out how to do this?

-Fred

---


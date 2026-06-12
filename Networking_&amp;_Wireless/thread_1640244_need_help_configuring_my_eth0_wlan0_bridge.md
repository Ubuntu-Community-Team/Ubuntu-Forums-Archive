---
title: "need help configuring my eth0 wlan0 bridge"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by jabberwok on 2010-12-07
I have my router downstairs and I have a belkin wireless G mimo usb network adapter connected to my lucid desktop upstairs (which worked out of the box, great!)

I also have a second computer and a router upstairs (using it as a switch).

Both computers are connected to the switch(I tried connecting them directly but neither recognize that a cable is plugged in)

I want to bridge my eth0 and wlan0 and provide internet to both computers upstairs.

here is my network/interfaces file, seems to set up the bridge and I can ping my router downstairs but neither computer gets internet

auto lo
iface lo inet loopback
address 127.0.0.1

auto br0

iface eth0 inet dhcp

iface wlan0 inet dhcp

iface br0 inet static
address 192.168.2.5
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255
bridge_ports wlan0 eth0
up \
/sbin/iwconfig wlan0 essid tux && \
/sbin/iwconfig wlan0 key <128bit hex key> && \
/sbin/iwconfig wlan0 channel 4 && \
/sbin/iwconfig wlan0 mode managed

any help much appreciated, thanks

---

### Post by jabberwok on 2010-12-07
can anybody help :D

---


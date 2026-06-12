---
title: "quick input on network setup"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by scales on 2009-06-13
hi all.  i have followed the tutorial: [https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint) to help me setup one of my computers as a router.  I had to tweak the network-interfaces file a little from theirs because i just have one ethernet(connected to the modem) and one wireless card which i broadcast out of.  here is what my network-interfaces file looks like 
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Gateway - 
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules

#Wireless Setup
auto wlan0
iface wlan0 inet manual
wireless-mode master
wireless-essid pivotpoint

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth0 wlan0

so i think everything is working but i no longer can ssh into the "routing" computer which i was able to do before.  my two questions are

1. is there a way i can get the ability to ssh into the routing computer back?
2. how can i add a wpa password to the wireless?

---

### Post by quixote on 2009-06-15
I don't know enough to answer your question, but have you already looked at wieman01's long thread? [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)  If it's not already answered somewhere there, that would be a better place to ask.  It's still active after more than 2 years!

---


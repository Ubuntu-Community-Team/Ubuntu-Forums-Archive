---
title: "How to connect Ubuntu server to wifi access point?"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by OlegVekhov on 2011-07-27
I'm using Ubuntu 11.04 Server and Atheros wireless card, managed by **iw** command.

Can anyone tell me how to connect my ubuntu box TO wifi WPA protected access point? Without stupid network managers and other hardweight tools. Just /etc/network/interfaces by hand... may be some guide?

According Google, seems that people only makes access points from their Ubuntu machines, but I need the reversed operation.

---

### Post by chili555 on 2011-07-27
If it's a server that you expect to ssh and ftp into, I'd suggest a static IP address. The address should be outside the range used by the DHCP server in the wireless access point. For example, I have my wireless router set to assign DHCP addresses from 192.16.1.100 to .110. My static machines use .115 and higher.

I assume the wireless card has drivers and is working well. If not, post back and we'll get that sorted out.

Then set up your /etc/network/interfaces file something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.115
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid <your_router>
wpa-psk <your_password>
```You will also need to set up DNS nameservers in /etc/resolv.conf, for example:```
nameserver 192.168.1.1
```Usually, the gateway is sufficient. You can use any nameservers you like, for example: [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

Test:```
sudo ifdown wlan0 && sudo ifup wlan0 
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---


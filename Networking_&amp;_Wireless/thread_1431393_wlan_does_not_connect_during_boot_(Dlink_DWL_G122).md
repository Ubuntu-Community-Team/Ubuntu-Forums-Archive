---
title: "wlan does not connect during boot (Dlink DWL G122)"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by klausmedk on 2010-03-16
Hello

I've installed ubuntu server 9.10 on a system using a DLink DWL G122 USB wlan adapter for connecting to my home network.

my interfaces file has this relevant content:

# The primary network interface
auto wlan0
iface wlan0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        wireless-mode managed
        wireless-channel 6
        wireless-essid my_essid
        wireless-key s:my_passphrase
        dns-nameservers 192.168.1.1

The adapter does however not connect automatically to my wlan during bootup.
If I however login on the system and type: 
"sudo iwconfig wlan0 key s:my_passphrase"
Everything works like a charm. So the adapter and the network works, it's just not connecting during boot-up.

Can anybody help me? 
Could this be the USB drivers not being loaded at the time network is started during boot?

//Klaus

---


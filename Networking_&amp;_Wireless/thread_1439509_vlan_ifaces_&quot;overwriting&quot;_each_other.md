---
title: "vlan: ifaces &quot;overwriting&quot; each other?"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by onineko on 2010-03-26
Hello!

I'm trying, and so far failing, to give my server access to different vlans.
I followed the ubuntu-howto and googled some more tips, but i'm stuck with this problem: whichever iface I write last in /etc/network/interfaces will work perfectly, but all others won't. it doesn't matter which one is last, either. on the switch, all VLANS are T on the required port.

what am I missing? 

(here the content of the /etc/network/interfaces in question)
auto lo
iface lo inet loopback

auto eth0
auto eth0.201
auto eth0.219


iface eth0 inet dhcp
#should get .20.197, und does

iface eth0.201 inet static
        address 192.168.1.200
        netmask 255.255.255.0
        network 192.168.20.0
        broadcast 192.168.1.255
        gateway 192.168.1.254
        dns-nameservers 192.168.20.251
        mtu 1500
        vlan-raw-device eth0


iface eth0.219 inet static
        address 192.168.5.249
        netmask 255.255.255.0
        network 192.168.5.0
        broadcast 192.168.5.255
        gateway 192.168.5.254
        dns-nameservers 192.168.20.251
        mtu 1500
        vlan-raw-device eth0

---


---
title: "if-up is not bringing up my devices"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by Curtor on 2009-07-16
H'Ok, so...

I have multiple NICs. One is my connect interface that has a static IP, and the others just look pretty.

Upon boot, I get the following message several times:
```
if-up.d/mountnfs [device__]: lock /var/run/network/mountnfs exist, not mounting 
```Where device is all but my connect NIC.

After boot, if I run "ifconfig", only my lo and connect NIC show up. If i run "ifconfig -a", all of my devices are there. I want all my devices to be up at boot though. If I run ifconfig <device__> up, the device will come up and work fine. I want it to work at boot with if-up though.

The /etc/networks/interfaces file should be fine, as it is the same that I used in my 8.04 machine, but regardless here it is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto connect
iface connect inet static
    address 192.168.x.y
    netmask 255.255.255.0
    network 192.168.x.0
    broadcast 192.168.x.255
    gateway 192.168.x.1

# Bring up sniff interfaces
auto device0 device1 device2 device3 device4
iface device0 inet manual
iface device1 inet manual
iface device2 inet manual
iface device3 inet manual
iface device4 inet manual 
```Any suggestions or requests for further debug information?

---


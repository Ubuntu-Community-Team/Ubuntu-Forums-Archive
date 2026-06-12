---
title: "Default gateway"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by ibob on 2009-01-19
Hi guys,

I have got an 8.10 ubuntu server and for some reason it never gets it's correct gateway.

My /etc/networks/interface says:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

> # The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.2.43
        gateway 192.168.2.1
        netmask 255.225.225.0
        broadcast 192.168.2.255
        network 192.168.2.0

which seems okay except when I restart the networking it says:

 > SIOCSIFNETMASK: Invalid argument
Failed to bring up eth0

I can't see what is invalid about that?  Also, eth0 does appear to have been brought up as it seems to work.

Anyhow, more annoying yet, the default gateway is incorrect. Whan I type 'route' i just get:

> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0

So, everytime I reboot the server I have to the following command to set the gateway:

 route add default gw 192.168.2.1 eth0

If there a way I can fix my networking? Thanks,

James

---

### Post by Kebabman on 2009-01-19
Your netmask looks wrong in your interface file :

You have :

255.225.225.0

It should be :

255.255.255.0

Hope this helps

---

### Post by ibob on 2009-01-19
Thanks. That was a great spot! Networking starting okay now.

Amazingly the gateway is fixed too.

Thanks,

James

---


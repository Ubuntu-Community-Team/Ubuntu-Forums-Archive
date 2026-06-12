---
title: "Openvpn problem"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2009-04-20
I have setup a test VPN which is working between one site and another. To add a complication both sites are using the same IP schema :(

However all seems to work. I have two devices on the remote site, 192.168.0.50 and 192.168.0.100. I can ping both of these devices locally, but only the .50 device across the network.

Here is the clients routes.

> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        *               255.255.255.255 UH    0      0        0 tun0
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
xxx.xxx.xxx.xx  192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.50    10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
192.168.0.100   10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


Can anyone help?

---

### Post by Peter09 on 2009-04-21
Bump

---


---
title: "[SOLVED] openvpn so near..."
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by phekdra on 2008-12-31
Hello, hopefully somebody can help me with my clueless newbie attempt to set up an openvpn connection between two remote ibex machines, both behind wireless routers. I've followed the instructions both on these forums and elsewhere and have successfully got the two machines to connect using the following configuration:

dev tun0
ifconfig 1.1.1.1 1.1.1.2
remote blah.com
secret /etc/openvpn/static.key
daemon

comp-lzo

user nobody
group nogroup
persist-key
persist-tun

ping-restart 60
ping 20

As I said, the two machines will connect - at least openvpn reports 'Initialization Sequence Completed'. I've opened port 1194 and 22 on both routers and forwarded them directly to the machines, and have enabled packet forwarding in the sysctl.conf files. I don't have firewalls running, apart from on the routers.

When I try and ping the remote IP, 1.1.1.2, I get a request timed out, same with ssh and http, and yet when I ssh directly via the internet to the remote machine I can do an ifconfig and see the RX packets and RX bytes increasing, so presumably traffic is arriving over the vpn link, but TX packets remains resolutely zero. So I'm stumped - can anyone shed some light?

Phekdra

---

### Post by phekdra on 2009-01-01
Well, here's the`result from tcpdump on the server after trying to first ping and then ssh to it from the client. Both attempts time out. Hopefully somebody will know what's going wrong.

12:38:08.576754 IP 1.1.1.1 > 1.1.1.2: ICMP echo request, id 1024, seq 20226, length 40
12:38:19.580428 IP 1.1.1.1 > 1.1.1.2: ICMP echo request, id 1024, seq 20482, length 40
12:38:42.280706 IP 1.1.1.1.1189 > 1.1.1.2.ssh: S 225992697:225992697(0) win 16384 <mss 1365,nop,nop,sackOK>
12:38:45.275666 IP 1.1.1.1.1189 > 1.1.1.2.ssh: S 225992697:225992697(0) win 16384 <mss 1365,nop,nop,sackOK>
12:38:51.291145 IP 1.1.1.1.1189 > 1.1.1.2.ssh: S 225992697:225992697(0) win 16384 <mss 1365,nop,nop,sackOK>


Phekdra

---

### Post by phekdra on 2009-01-01
Okay, here's the routing table on the openvpn server I'm connecting to.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.1.1.2         *               255.255.255.255 UH    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by phekdra on 2009-01-01
It works! I've no idea why but I'm so happy!!! :D

Phekdra

---

### Post by Iowan on 2009-01-01
Glad it works - you got SO much help :---) VPN is still on my To-Do list. If it *stays* fixed, mark the thread [SOLVED] (Under Thread Tools).

---

### Post by phekdra on 2009-01-01
> **Iowan said:**
> Glad it works - you got SO much help :---) VPN is still on my To-Do list. If it *stays* fixed, mark the thread [SOLVED] (Under Thread Tools).

:D Will do. I think it was because there was an inconsistency between the ip addresses I'd chosen on the two connected machines. I changed machine A to use 1.1.1.1 and machine B to use 1.1.1.2 and lo and behold pings returned, ssh connected, and vnc became visible. Time for some celebratory champagne - it is new year's day after all. :tongue:

Phekdra

---


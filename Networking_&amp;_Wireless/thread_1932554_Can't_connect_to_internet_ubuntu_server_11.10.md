---
title: "Can't connect to internet ubuntu server 11.10"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by LiefhebberLinux on 2012-02-27
I have installed Ubuntu Server 11.10 today on a Dell T410 server for a home server installation. I ran into a problem with my networking. Network authorisation using DHCP failed after which I moved to manual configuration which I did as follows:

Computer IP: 192.168.0.120
netmask: 255.255.255.0
gateway: 192.168.0.1 (this is on my router (Virgin Media))
nameservers I left blank (possibly an error)

After finishing my installation I can't access the internet

ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
ping 74.125.43.147
From 192.168.0.120 icmp_seq=2(3,4,5,etc) Destination Host Unreachable
ping localhost
64 bytes from localhost (127.0.0.1) icmp_req=1 tt1=64 time= ...ms
ping 192.168.0.2 (other pc connected to my router)
From 192.168.0.120 icmp_seq=2(3,4,5,etc) Destination Host Unreachable

I haven't used my WAN xx.xx.xxx.xx anywhere.

Any pointers would be appreciated

---

### Post by Iowan on 2012-02-27
Looks like a DNS probem. Try adding one (like 8.8.8.8).

For what it's worth, most of my servers, printers, etc., get a DHCP address - although the DHCP server is set to give them the same address each time (static lease).

---


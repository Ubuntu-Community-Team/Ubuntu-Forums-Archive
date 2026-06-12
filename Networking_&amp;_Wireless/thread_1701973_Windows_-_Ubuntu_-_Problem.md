---
title: "Windows - Ubuntu - Problem"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by pk110954 on 2011-03-07
Hello everybody I wanted to setup up a little Network with an Windows 7 Machine and an Ubuntu 10.10 Machine. These Computers are connected over the interface eth0 with an Switch.

Now, i configured these Machines with the following COnfiguration:

**Windows:**
eth0: IP: 192.168.200.20 
         Netzmask: 255.255.255.0
         Gateway: 192.168.200.10    -> IP from the Linux Machine
         IPv6: 2001:470:1f00:ffff::189/64
                  IPv6-Gateway: link local IPv6 from the Linux Machine

**Linux:**
eth0: IP: 192.168.200.10
         Netmask: 255.255.255.0
         Gateway: 192.168.200.20      -> IP fro the Windows Machine
         IPv6: 1001:470:1f00:ffff::189/64
                  IPv6-Gateway: link local from the Windows Machine

IPv6 Routes under Windows and Linux are also added!

Now I tested this Configuration with ping and ping6 !
I can ping with IPv4 and IPv6 from the Windows Machine to the Linux Machine, but the ping fails if I want to ping from Linux to WIndows.
I also tested if, without Gateways, but it doesn't work!



Did somebody have an Idea what I make wrong or what i Could do that this Szenario will work !


Greetz
Patrick

---

### Post by lncoll on 2011-03-07
May be the firewall in your Windows PC is locking ping requests.
Go to firewall and uncheck ping or echo (don't remenber) in the ICMP tab.

---


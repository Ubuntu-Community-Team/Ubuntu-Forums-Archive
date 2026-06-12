---
title: "Bridging two of three Ethernet connections"
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by TheHammer101 on 2013-03-17
I have a fresh install of Ubuntu Server 12.04, I've added a password for the  root user so I can type commands a little faster, installed bridge  utilities with "sudo apt-get install bridge-utils",  I made "eth0" dhcp (which is working correctly), and created a bridge  "br0" with a static IP using "eth1" and "eth2". PC #1 and #3 are able to  communicate. This is literally all I have done. Now from my  understanding since I haven't set up any sort of forwarding to my  knowledge these two networks are completely separate, and shouldn't be  able to access each other, right?

Apparently not, because PC #2  can SSH into the "br0" IP (192.168.0.10), and PC #1 and #3 can SSH into  "eth0" (192.168.0.122). I want "br0", and "eth0" networks separate, and don't  understand why, or how this is even happening since I haven't even un-commented the line to forward ipv4 addresses..

*edit* PC #2 cannot access PC #1, or PC #3. Which is fine, and how I'd like it. PC #1, and #3 can't reach PC #2 as well.


[IMG]http://denieru.no-ip.org/pics/map.jpg[/IMG]

---

### Post by Doug S on 2013-03-17
Everything is on the same sub-net so there is nothing to "forward".
Try changing br0 and pc1 and pc3 to 192.168.234.0 sub-net (mask 255.255.255.0), and where the "234" can be any integer from 1 to 254.

Edit: assuming the 192.168.0.0 subnet mask is 255.255.255.0. If not then tell us what it is.

---

### Post by TheHammer101 on 2013-03-17
Why would it being on the same sub-net matter though? They are on different interfaces, so wouldn't that separate them? If I change the subnet of PC #1, PC #3, and "br0" so that they are 192.168.1.1 192.168.1.2 192.168.1.3 would they become inaccessible even if I tried to SSH into that "br0" IP (192.168.1.3) from PC #2 (192.168.0.122)? For instance if I am running a DHCP server on "br0" (192.168.1.3) won't that spill over onto "eth0" (192.168.0.122). I tried running a setup like that before, and it was creating problems for PC #2 being able to connect to the router. I think it was getting DHCP from "br0" (192.168.1.3) while switching between that and the DHCP from the router (192.168.0.1)...

---

### Post by Doug S on 2013-03-17
> Why would it being on the same sub-net matter though? They are on different interfaces, so wouldn't that separate them?I'm not sure, but based on what you have said i'm guessing that somehow your Ubuntu server is figuring it out.> For instance if I am running a DHCP server on "br0" (192.168.1.3) won't that spill over onto "eth0" (192.168.0.122).I do not see how. Just make sure that your DHCP server is only listening to br0 and not all interfaces.> If I change the subnet of PC #1, PC #3, and "br0" so that they are 192.168.1.1 192.168.1.2 192.168.1.3 would they become inaccessible even if I tried to SSH into that "br0" IP (192.168.1.3) from PC #2 (192.168.0.122)?PC #2 would not have any idea how to get to br0. It wouldn't know the route.

Edit: see the file /etc/default/isc-dhcp-server for dhcp server listening interfaces list, which defaults to all.

Edit 2: By the way, It is not clear to me why you would run a DHCP server on your Ubuntu server. Your diagram seems to indicate that everthing on br0 is setup manually.

---

### Post by TheHammer101 on 2013-03-20
So, I have no idea why being on the same subnet mattered. When I set up  my server with a "br0" IP (1.1.1.1) manually, made PC #1 (1.1.1.100)  manually,  and made PC #2 IP (1.1.1.10) manually I could not reach the "br0" IP  (1.1.1.1), or PC #1  IP (1.1.1.100) from PC #2 IP (1.1.1.10) unless I had set up iptables to  forward correctly. Then I set up DHCP and DNS servers on "br0". Thanks  for your help, but I'm still confused as to why it makes a difference  that they are on the same subnet.

[IMG]http://denieru.no-ip.org/pics/map2.jpg[/IMG]

---


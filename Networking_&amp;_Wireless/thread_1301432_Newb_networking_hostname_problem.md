---
title: "Newb networking hostname problem"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by OriginalAdric on 2009-10-26
I'm running a LAN on a dlink router with two windows machines and a freshly installed Ubuntu machine. When I try to ping the Ubuntu machine's host name from the windows machines, the name doesn't resolve (tho pinging the IP address works fine).

I've searched the forums with my limited understanding of the terms I need to know and vague source of the problem, and I haven't been able to find a solution. I'm a complete beginner at linux, and my technical experience is fairly limited, so I'm going to need a relatively simplified answer for me to understand what to do.

Hre's what I know about the problem and some solutions I've tried:

The router registers the ubuntu machine's MAC address with its computer name on its "Dynamic DHCP Clients List." The /etc/hostname file is using the host name I want. I tried editing the /etc/dhcp3/dhclient.conf file as per some of the other threads.

If there's other information that would be more helpful in solving my issue, please tell me what it is and how to find it.

---

### Post by Iowan on 2009-10-26
Quick/dirty method is to put an entry in the *hosts* file of the Windows machines (I don't remember the path, though)

---

### Post by OriginalAdric on 2009-10-27
I found the file and took a look in it, and the immediate issue I'm finding is that for it to be effective, I have to have static IPs for the machines that I put in the file. I'd like to avoid assigning static IPs and just let  the router take care of the network configuration. If there's no way around it, then static IPs it is, but I want to exhaust a few more fixes first.

---

### Post by Iowan on 2009-10-27
I switched to **dnsmasq** for DHCP/DNS server because it ties the two together - I can ping machines on my network by hostname - even though they have DHCP address. Dunno if any routers have that function built in.

---


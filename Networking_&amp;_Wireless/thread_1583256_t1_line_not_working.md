---
title: "t1 line not working"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by ishokenmei on 2010-09-27
My T1 connection is like this: T1 line -- cisco router -- regular router -- LAN.  It works fine.  Now I want to replace the regular router with an Ubuntu router, which has two nic card, eth0 to Internet and eth1 to LAN.  I tested the Ubuntu router on a DSL connection and it worked perfectly.  But when I connected the cable from the cisco router to eth0 in the Ubuntu router, eth0 was not up.  It didn't show the ip address of eth0 as I tried "ifconfig".  I assigned the static ip from the ISP to eth0, also made it acquire ip automatically.  Neither worked.  eth0 still got no ip address. Did I miss something?
Thanks in advance.

---

### Post by ishokenmei on 2010-09-28
anyone?

---

### Post by dineshs on 2010-09-29
Did you try a different cable(straight/cross)

---

### Post by SeijiSensei on 2010-09-29
Is eth0 defined with a static address in /etc/network/interfaces or do you have "iface eth0 inet dhcp" instead?

Probably what happened is when you connected to the ISP directly, the box got its IP address from the ISP via DHCP.  I'd bet the Cisco isn't configured to run a DHCP server itself.  

You'll need to [assign a static address]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") to eth0, and one which is in the same network space as the inward-facing interface on the Cisco.  So if the internal Cisco interface is 192.168.1.1, assign eth0 on your box an address like 192.168.1.2, and make the Cisco be the default gateway for the Ubuntu box.

I presume that you're using a hub or switch into which both the Cisco and the Ubuntu box are connected.  If you're just wiring them together, then as dineshs says you'll need a "crossover" cable.  Since whatever method you were using before to connect the internal router to the Cisco was working, replicate that method with the Ubuntu router.

---

### Post by ishokenmei on 2010-09-29
Thanks guys. Yes, it's a crossover cable that connects cisco router and ubuntu box.  I tested the cable on the other machine and it works fine.   eth0 is configured as static, with ip, gateway, netmask,etc from the ISP.  but somehow eth0 didn't get the ip.

---

### Post by SeijiSensei on 2010-09-30
> **ishokenmei said:**
> Thanks guys. Yes, it's a crossover cable that connects cisco router and ubuntu box.  I tested the cable on the other machine and it works fine.   eth0 is configured as static, with ip, gateway, netmask,etc from the ISP.  but somehow eth0 didn't get the ip.

You can't use the ISP's address information on the Ubuntu box.  As I said, it needs to have an IP address in the same space as the **internally-facing** Cisco interface.  The Cisco has the ISPs addressing on its externally-facing interface.  What address does its internal interface have?  You need to use an address on the Ubuntu box that's consistent with that Cisco address.

---

### Post by ishokenmei on 2010-09-30
> **SeijiSensei said:**
> You can't use the ISP's address information on the Ubuntu box.  As I said, it needs to have an IP address in the same space as the **internally-facing** Cisco interface.  The Cisco has the ISPs addressing on its externally-facing interface.  What address does its internal interface have?  You need to use an address on the Ubuntu box that's consistent with that Cisco address.
I logged in the regular router (Netgear) used to connect to cisco router and checked its WAN port setting.  The WAN port uses the IP info from the ISP and the routing table doesn't have any route that looks like cisco's internal interface.  This router works fine when it's hooked up with cisco router.  I wonder if Ubuntu box should use the same setting for eth0. 
It's my first time using cisco router.  How do I check its IP?

---

### Post by SeijiSensei on 2010-09-30
> **ishokenmei said:**
> I logged in the regular router (Netgear) used to connect to cisco router and checked its WAN port setting.  The WAN port uses the IP info from the ISP and the routing table doesn't have any route that looks like cisco's internal interface.  This router works fine when it's hooked up with cisco router.  I wonder if Ubuntu box should use the same setting for eth0. 
It's my first time using cisco router.  How do I check its IP?

Ah, I bet your ISP routes an IP subnet to you rather than a single address.  In these cases the router will take one of the addresses for itself and route the remainder to other devices.  So, yes, you should replicate the configuration of the Netgear on the Cisco-facing interface of the Linux box.

---

### Post by ishokenmei on 2010-10-01
> **SeijiSensei said:**
> Ah, I bet your ISP routes an IP subnet to you rather than a single address.  In these cases the router will take one of the addresses for itself and route the remainder to other devices.  So, yes, you should replicate the configuration of the Netgear on the Cisco-facing interface of the Linux box.

ifconfig showed that eth0's ip and other info were the same as Netgear, but it returned "unknown host" when I pinged google and its ip.  DNS server was set up and works.  Any idea?

---

### Post by SeijiSensei on 2010-10-01
See if you can ping this address:  173.194.35.104.  "Unknown host" means that the DNS resolver on this computer couldn't determine the address for [www.google.com](www.google.com).  With a static IP you'll usually need to tell the resolver where the DNS servers are by creating /etc/resolv.conf manually.  It should look like this:

domain example.com
nameserver 10.10.10.10
nameserver 10.10.10.11
search example.com example.net

The domain and search parameters tell the system what domain(s) to append to "unqualified" names like "host1".  Replace these entries and the nameserver addresses with the correct ones for your network setup.  "man resolv.conf" will have more details.

---

### Post by ishokenmei on 2010-10-01
> **SeijiSensei said:**
> See if you can ping this address:  173.194.35.104.  &quot;Unknown host&quot; means that the DNS resolver on this computer couldn't determine the address for [www.google.com]("http://www.google.com").  With a static IP you'll usually need to tell the resolver where the DNS servers are by creating /etc/resolv.conf manually.  It should look like this:

domain example.com
nameserver 10.10.10.10
nameserver 10.10.10.11
search example.com example.net

The domain and search parameters tell the system what domain(s) to append to &quot;unqualified&quot; names like &quot;host1&quot;.  Replace these entries and the nameserver addresses with the correct ones for your network setup.  &quot;man resolv.conf&quot; will have more details.

the resolv.conf was edited to use the DNS server before I pinged google.  Since I don't have the access to the ubuntu box now, I'll try the ip and double check the setting once I have it.

---

### Post by ishokenmei on 2010-10-07
> **SeijiSensei said:**
> See if you can ping this address:  173.194.35.104.  &quot;Unknown host&quot; means that the DNS resolver on this computer couldn't determine the address for [www.google.com]("http://www.google.com").  With a static IP you'll usually need to tell the resolver where the DNS servers are by creating /etc/resolv.conf manually.  It should look like this:

domain example.com
nameserver 10.10.10.10
nameserver 10.10.10.11
search example.com example.net

The domain and search parameters tell the system what domain(s) to append to &quot;unqualified&quot; names like &quot;host1&quot;.  Replace these entries and the nameserver addresses with the correct ones for your network setup.  &quot;man resolv.conf&quot; will have more details.

It's been a while since last post.  I was so busy that I didn't get a chance to test it as advised.  Anyway, when I pinged 173.194.35.104, it showed "Destination Host Unreachable".  The setting of resolv.conf is working fine since I tried the machine on other Internet connection with a static ip assigned to eth0 as well and I was able to ping the ip.  It looked like eth0 didn't connect to the Internet.

---


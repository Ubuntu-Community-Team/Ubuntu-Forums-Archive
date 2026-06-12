---
title: "Need help setting up hardy server as router"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by charliemyboy on 2009-04-29
I'm trying to setup an ubuntu server (hostname "ubuntu") for web development using a Windows XP client. The XP box has only one ethernet card and the ubuntu box has two. I'm trying to use ubuntu interface eth0 to access the internet and eth1 to connect to the XP box.  It mostly works.  From XP I can ssh to ubuntu or access apache on ubuntu via browser.  What I want to do is be able to browse the internet from XP using ubuntu as a router.  Here's my routing table--

[FONT=Courier New]cdev@ubuntu:~$ route
Kernel IP routing table
Destination   Gateway                Genmask           Flags Metric Ref    Use Iface
71.134.240.0    *                         255.255.255.0   U         0        0         0   eth0
10.1.1.0             *              255.255.255.0   U        0        0         0   eth1
default           adsl-71-134-240 0.0.0.0               UG       100   0         0   eth0[/FONT]

My sysadmin skills are pretty rusty and were developed on Solaris rather than Linux, but this looks like it should work to me.  I am able to access the internet from ubuntu on eth0 and communicate between ubuntu (eth1 IP addr 10.1.1.1)  and XP (IP addr 10.1.1.2) on eth1.  The eth0 subnet connects to my dsl router which uses dhcp and gives ubuntu its IP address and DNS server.  Ubuntu is not running either apache or a DNS server.  I check resolv.conf to get the DNS server address and manually enter that in network setup on XP with 10.1.1.1 as the gateway.  XP can talk to ubuntu via ssh but can't access the nameserver when I try to browse.  I get "Address not found" from Firefox on XP.

One thing that seems a little wierd is that I can ping 10.1.1.1 from XP but cannot ping 10.1.1.2 from ubuntu even though I can see it in the routing table and ssh works fine.

Can anyone point me in the right direction here?  I am using the Hardy server edition.

Thanks

---


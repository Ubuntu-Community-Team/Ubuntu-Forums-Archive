---
title: "Static IP Address"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by MCAccord on 2009-01-04
Hey everyone. I've got a question here. I'm trying to setup a static IP address on my 8.10 Ubuntu. I finally got it setup to be static, but now I can't get online. Here's kind of what I got going. So the Ubuntu is on a Windows network running Server 2003. This server controls Active Directory, DNS, and DHCP. I've got this connected to a linksys wireless router that is not handling DHCP and DNS and I turned this feature off. Server 2003 has a static IP of 10.1.1.100. When I connect a laptop to this network it gets an IP and can connect just fine to the internet (which surprised me... a LOT!). Server 2003 can connect just fine to the internet, and so could Ubuntu when it had an automatic address. Here's what's going on on the Ubuntu box:
IP: 10.1.1.250/24
Gateway: 10.1.1.1 (Linksys wireless router)
DNS: 10.1.1.100
Doesn't that make sense? I think my problem lies with the DNS, but I can't figure out what I need to change to get that computer online again.
Thanks for the help!

---

### Post by hal8000 on 2009-01-22
See this post::
[http://ubuntuforums.org/showthread.php?t=1018537](http://ubuntuforums.org/showthread.php?t=1018537)

Its a bug in 8.10 uninstall network manager, manually assign a static IP address and networking will be ok.

---

### Post by MCAccord on 2009-01-22
Yeah, I ended up getting it to work. I went and manually configured the .conf file, can't remember the name, and then all it needed was a simple reboot. It appears that I don't even use the built in network manager anymore, until I change the .conf to auto again, I don't believe I will be able to use it. It works fine though. Thanks for the help!

---


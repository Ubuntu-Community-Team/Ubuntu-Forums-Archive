---
title: "Assigning the same internal IP address to a laptop"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by bruparel on 2009-04-23
I have three laptops all running Ubuntu 8.10.  I use at least one as a server to test my ruby on rails applications.  Problem is it gets reassigned a different IP address frequently, e.g., 192.168.1.104 (105, 107 and so on).  All public private keys are invalid then and if I try to ssh into that machine ssh thinks that a man in the middle attack is going on!
I would like to make sure that the same IP address gets assigned to the same machine so I don't run into these problems.  Now I have a LinkSys wireless router so I know that I am using dhcp, but is there a way to make sure that the same "internal" IP address gets assigned to the same machine?
Thanks.
Bharat

---

### Post by mozetti on 2009-04-23
You could intall an alternative firmware to your Linksys router. I use DD-WRT and know that it has the option to set static dhcp leases - assigning the same ip to the same machine using dhcp.

Other firmware, like OpenWRT and tomato may do this, too.

---

### Post by SmoothDetonator on 2009-04-23
If you want to assign a static ip to each computer there are two ways to do it.  You can do this through your router, similar to the method the above poster mentioned, or you can assign a static ip on each computer.

I would recommend setting up your network so that you have a range for dynamic IPs and a range for static IPs.  For example, you can use the range 192.168.1.100 to 192.168.1.149, and use your router to assign IPs through dhcp.  Then start your static IPs at 192.168.1.150.  Assign the first laptop to 192.168.1.150, assign the next to 192.168.1.151, and so on.

Below is a link that explains how to set up a static IP in 8.10.  As the article states, it can be a bit buggy, so some patience may be required:
[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---


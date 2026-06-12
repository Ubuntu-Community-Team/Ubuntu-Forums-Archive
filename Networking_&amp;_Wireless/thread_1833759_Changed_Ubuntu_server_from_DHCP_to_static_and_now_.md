---
title: "Changed Ubuntu server from DHCP to static and now cannot access web..."
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by ChipGibblets on 2011-08-26
I assigned a static ip to my Ubuntu Server machine and it cannot access the web now.  It can access anything on the LAN.  The other two nodes on the network (one wifi one hardwired) can both access the web just fine.  

First post.  If this is in the wrong area, I apologize...

---

### Post by gordintoronto on 2011-08-26
You got the right area!

I think that by using static instead of DHCP, the machine no longer gets a DNS from your router. The DNS is stored in /etc/resolv.conf, so this command will display it:
cat /etc/resolv.conf

It should contain two lines which look like this:
nameserver 55.5.20.20

Or whatever DNS servers your ISP has told you to use.

When you use DHCP, resolv.conf is created every time you boot. I don't think yours is ever getting created.

---


---
title: "Wicd and Static IP, can't get DNS to work"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2009-07-28
I'm using Wicd 1.5.9 on Kubuntu 9.04.  I'm connecting over wifi to a Linksys WRT54G, with Comcast broadband.  Everything works great when I use DHCP, but when I try to set Wicd to use static IP, I have problems with DNS.  

Here are my settings in Wicd:

IP: 10.0.0.2
Netmask: 255.255.255.0
Gateway: 10.0.0.1

With this setting, and nothing static set for the DNS, it'll work for a little while and then DNS lookups stop working.

If I set the static DNS to 10.0.0.1, the same is true.

If I set them to the comcast DNS that the router reports, e.g. 68.87.72.134, it's weirder.  I can't get to anything in a web browser, but I can ping that DNS server, and also nslookup still works.  

I'm sharing my printer and some file shares off this machine so it's easier if I can get static IP to work, otherwise I keep have to remove and re-add the printers on the other client machines whenever I reboot this one.  (every day - my uptime fetish has been trumped by my eco-conscience ;)

---

### Post by superprash2003 on 2009-07-28
try with opendns servers - 208.67.222.222 .. also post output of nslookup and a ping to say google.com

---

### Post by skullmunky on 2009-07-28
thanks, it's working now - strangely, with either the opendns or comcast's server.  I'll post back again if it stops working ...

---


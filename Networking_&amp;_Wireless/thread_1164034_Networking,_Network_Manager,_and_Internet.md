---
title: "Networking, Network Manager, and Internet"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2009-05-19
Hello,

I am having problem surfing the internet (it is so slow). It just keeps looking for the page with no help. Below is some facts that might help:

[LIST=1]
[*]The same computer when booted on WinXP, works OK.
[*]I can ping the DSL router fine.
[*]my resolv.conf file shows the IP address of the router
[*]I do not have network manager installed since last version as it had problems
[*]When I used my Broadband connection (Bandlux) using my SIM card, ubuntu internet is ok
[/LIST]

---

### Post by superprash2003 on 2009-05-19
you could try using opendns servers - 208.67.222.222 and 208.67.220.220 . 
other things you could try
1)disable ipv6
2)change MTU values

---

### Post by Iowan on 2009-05-19
I never got Intrepid installed on a machine, but (so far) I've been pleased with Jaunty's Network Manager.  I installed it on a notebook, and it connects via wireless when requested; auto-connects via wired, or (if DHCP isn't working) falls back to a static IP address I set up. 
 DNS, IPv6 and MTU might still cause problems, though...

---

### Post by OOzypal on 2009-05-20
How can I disable ipv6. Moreover, I always looses my resolv.conf. Is the network manager ok now. Do I need to install it? 

Thank you

---

### Post by superprash2003 on 2009-05-20
disable ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

resolv.conf will overwrite if you use dhcp..

---

### Post by Iowan on 2009-05-20
IF you want to use DHCP, but want to use your choice of DNS servers, you can give them preference by editing this line in /etc/dhcp3/dhclient.conf ```
#prepend domain-name-servers 127.0.0.1;

```Uncomment the line and use your DNS servers instead of 127.0.0.1. (separated with commas?)

---


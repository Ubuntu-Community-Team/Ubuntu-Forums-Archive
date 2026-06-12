---
title: "Ip tables and masqurading a single ip differently than the rest"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by JeppeM on 2009-07-16
Hey all,

I have a gateway machine i have test up using Ebox, and it works perfectly for our internal networks to access the internet. However, now i need one machine (internal 192.168.22.5) to get a different IP when it accesses the internet... Ie: All clients are currently set to be masquerade to ip 80.63.35.xxx, but this 22.5 server I would like to appear on the internet as 83.91.83.xxx.

I have no idea how to do this, since ebox has setup most of the things on the server... With the right iptables common i would probably be able to figure it out though.

Hope someone can help me :) Thanks,
Jeppe

---

### Post by DGortze380 on 2009-07-16
The correct term for what you're describing is NAT (Network Address Translation). That should help you in your search.

First Google Hit: [http://www.howtoforge.com/nat_iptables](http://www.howtoforge.com/nat_iptables)

You can do this with a Virtual NIC if you're short on Network Cards.

---

### Post by JeppeM on 2009-07-19
Ah, cool :) I'll try to look into it... One more question though... I remember that last time i played around with iptables, i had a hard time getting eth0:1 to be reconized.. In this case, i know that Ebox has set up the system to Masquerade everything coming out of eth0, which makes sense. But for this single server, i'd like the connections to go out of eth0:7 (i have 9 external ips in total).

Am i remembering right, that it's not just typing eth0:7 when i want to refer to that interface? Do i need to escape the : or something? :)

Thanks a lot for your help.

---

### Post by DGortze380 on 2009-07-19
It appears that iptables does not support virtual interfaces: [http://www.linuxquestions.org/questions/linux-security-4/iptables-and-virtual-interfaces-201220/](http://www.linuxquestions.org/questions/linux-security-4/iptables-and-virtual-interfaces-201220/)

All traffic to and from eth0:0-8 will appear to iptables as if it's traffic on eth0. Construct your rules accordingly or add more physical NICs.

> 
If you want to deal with aliases in Netfilter, you'll have to filter
using both interface and alias IP :

        iptables -A INPUT -i eth0 -d <eth0:2 IP> ... -j ACCEPT ****

[http://www.derkeiler.com/Mailing-Lists/securityfocus/focus-linux/2002-01/0094.html](http://www.derkeiler.com/Mailing-Lists/securityfocus/focus-linux/2002-01/0094.html)


---

### Post by JeppeM on 2009-07-21
Yay! Got it to work... I had a big fight with it because i added my rule after something which already caught everything... But after editting the right file to add my rule before the other one, it works like a charm... Thanks a lot for your help.

---


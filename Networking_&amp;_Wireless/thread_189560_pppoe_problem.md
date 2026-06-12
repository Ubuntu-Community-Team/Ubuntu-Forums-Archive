---
title: "pppoe problem"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by Amar_ze on 2006-06-05
I have this really 'stupid' problem. I have ADSL connection via DHCP. I got nameservers automaticly from ISP.Now problem is that every 2 hours (aprox.) connection just dies.I can't open any site ( well I can but when I conntact that site thru IP not thru host) so I am guesing it's DNS problems.On windows everything works fine so it's not my ISP's issue. I setup my conn. with pppoeconf and I start it with pon dsl-provider and stop it with poff ( as pppoeconf said).Maybe someone had same problem and can help me.Will be thankful. Regards :)

Edit: when connection dies and I run ifconfig I can see ppp0 with IP and all seems OK

---

### Post by xbadger on 2007-02-12
I have the same problem. Try:
sudo ifdown eth0
sudo ifup eth0
and then try sudo pppoeconf

I see no one here knows what the problem is, maybe a bug. :(

---


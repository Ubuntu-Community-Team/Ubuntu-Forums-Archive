---
title: "Network Load balance with 8 ADSL links"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Vladimir Hidalgo on 2010-08-24
Hi, I've got 9 ADSL links and I would like to do Network load balance.

My setup is as follows:

9 x 1Mbps ADSL Links
9 x ADSL modem/router
1 x 24 ports switch
1 x Ubuntu server connected to above mentionated switch
20 x Lubuntu clients connected to above mentionated switch


Now my problem is that I'm unable to find a motherboard with 9 PCI to have 9 physical NICs. I may add 3 more lines in a month or so, so I think a motherboard with 12 PCI slots would be hard to find...

So, I wonder is there's possibility to do this:



```

ADSL1 ADSL2 ADSL3 ADSL4 ADSL5 ADSLx
  |     |     |     |     |     |
 ______________________________________
|                                      |
|               Switch                 |
|______________________________________|
                  |
                 NIC1
 ______________________________________
|                                      |
|         Server/load balance          |
|______________________________________|
                 NIC2
                  |
 ______________________________________
|                                      |
|               Switch                 |
|______________________________________|

  |     |     |     |     |     |
 PC1   PC2   PC3   PC4   PC5   PCX

```


This would eliminate the need of adding 1 NIC per ADSL line.

Now, it's possible to do load balacing not between physical NICs but between a pool of ADSL connections in the switch, I guess by IP?

Thank you

---

### Post by BkkBonanza on 2010-08-24
You should be able to do that as long as the bandwidth of the network is suffcient. You would need just adsl modems, not full router capabilties on each one. Not that it matters but they could be cheaper.

You should be able to setup the load balancing to route to the IP for each adsl gateway. I haven't had to do this myself but I think it's doable. That is, I believe you can set the route commands by IP via same IF.

eg. 
ip route add default scope global nexthop via $IP1 dev $IF1 weight 1 nexthop via $IP2 dev $IF1 weight 1

Anyway, it's easy to test it out. Just use your current inside switch on the outside and test how it works. If ok, then buy another switch.

---

### Post by Vladimir Hidalgo on 2010-08-24
Thank you, ISP already provided me with one ADSL wireless router per line for free, I will turn off wireless and use only 1 port so I can use them for the task :)

Anyway, I'm a little bit lost when it comes to the package/software I need to use in order to setup the load balance.

I've reviewed [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) or [https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation) but only "NICs" can be "Slaves" as it seems.

If I could use the ADSL router's IP as "Slave" I think I would be done.

----------------------

Edit: I'll look more about the **ip route** command, I don't quite get all the sintaxis, but I guess it's a short (only 2 IPs) of what I need.

Thanks for the hint, I'll try right now!

---

### Post by Vladimir Hidalgo on 2010-08-25
I will try this:
```
ip route add default scope global nexthop via 192.168.1.2 dev eth2 weight 1 nexthop via 192.168.1.3 dev eth2 weight 1 nexthop via 192.168.1.4 dev eth2 weight 1 nexthop via 192.168.1.x dev eth2 weight 1
```

Where Eth1 will be connected to inside switch and Eth2 to outside switch.

---

### Post by BkkBonanza on 2010-08-25
That is only part of the config. I got that from this page,

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

And I used it once before but not exactly how you want to do it. This isn't using bonding though and I'm not sure if it's possible with one interface using bonding. Likely not as it seems that is used when you want to bond multiple interfaces. In the above solution the balancing is handled by routing tables instead of interface bonding.

---

### Post by Vladimir Hidalgo on 2010-08-25
I don't really need a big pipe, it's just that the 20 clients need to be in the same local lan, have internet access and access some files in the server

So I need to somehow make the server distribute the network (internet) load from the 20 PCs between the 9 ADSL lines.

Also this setup will allow me to restrict some webpages.

So it does  not matter if traffic goes out from multiples IPs, but to balance across them.

Thank you.

---


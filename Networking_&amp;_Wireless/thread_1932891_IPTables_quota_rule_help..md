---
title: "IPTables quota rule help."
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by ayenack on 2012-02-28
Hello all.

I'm trying to set up an iptables rule to set a quota for my mobile broadband to 15GB a month and need some help. I'm not at all good with iptables and need some help with the quota rule. Here's what I'm planning to do.

```
iptables -N PPP0-QUOTA
iptables -A INPUT -d 127.0.0.1 -j PPP0-QUOTA
iptables -A INPUT -s 127.0.0.1 -j PPP0-QUOTA
iptables -A PPP0-QUOTA -m quota --quota 15360 -j ACCEPT
iptables -A PPP0-QUOTA -j REJECT
```

I want it to just apply to ppp0 but as I have it it'll apply to all interfaces. My inclination is to just stick ppp0 at the end of each rule but I don't think that's a good idea can anyone explain how to apply the rule to just ppp0.

Thanks for any help.

ayenack.

---

### Post by kevdog on 2012-02-28
Could you list ifconfig?

---

### Post by ayenack on 2012-02-28
Of course.

eth0      Link encap:Ethernet  HWaddr 14:da:e9:04:48:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33840 (33.0 KiB)  TX bytes:33840 (33.0 KiB)

ppp0      Link encap: Point-to-Point Protocol  
          inet addr:188.28.58.103  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3967026 (3.7 MiB)  TX bytes:581510 (567.8 KiB)

---

### Post by kevdog on 2012-02-28
I believe it would be something like this:

iptables -A PPP0-QUOTA -i ppp0 -m quota --quota 15360 -j ACCEPT 
iptables -A PPP0-QUOTA -i ppp0 -j REJECT

---

### Post by ayenack on 2012-02-28
As usual kevdog your advice on networking issues is spot on.

Thanks very much it works perfectly.

ayenack.

---

### Post by SeijiSensei on 2012-02-28
I've never seen the quota rule before.  Does iptables write the current traffic totals to disk each time you shut the machine down?  Otherwise how would it know what the cumulative traffic figure is?

Obviously if the computer is up and running full time like a router or server, this would work well.  I just never thought of iptables as being able to save state through reboots.

---


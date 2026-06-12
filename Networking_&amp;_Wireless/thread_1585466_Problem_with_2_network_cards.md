---
title: "Problem with 2 network cards"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by larry.said on 2010-09-30
I have 2 network cards. I configured one and it works fine (Auto eth1) which connectes to the internet via a router through a DNS server. 

Now if I create a new connection, Auto eth0 and configure that one to connect directly to another computer (i.e. not through the router) it connects fine as well.

However, if I try to ping my computer through eth1 from another PC on the network I get no answer. Yet both eth1 and eth0 are connected. 

Note: eth0 and eth1 have the same subnet mask but different IPs. If i disconnect eth0 and try pinging eth1 again, that time it works. If i now reconnect eth0 and try pinging, it doesn`t

Any suggestions?

---

### Post by SeijiSensei on 2010-09-30
[http://ubuntuforums.org/showpost.php?p=9873817&postcount=2](http://ubuntuforums.org/showpost.php?p=9873817&postcount=2)

---

### Post by larry.said on 2010-09-30
I tried enabling packet forwarding but this did not do anything.

If this helps: Auto eth1 was available by default when I booted my system. However Auto eth0 was not, I had to create it.

---

### Post by SeijiSensei on 2010-09-30
As a guess, your router may need a static route that points to the network address shared by eth0 and the computer you're trying to ping with the address on eth1 as the gateway.

---

### Post by larry.said on 2010-09-30
hmm I think I may not have explained the situation properly. The thing is, computer A has 2 network cards eth0 and eth1. eth1 is connected to a router and eth0 is connected to computer B which only connects to computer A and no other computer. Therefore eth0 and eth1 are completely independent. 

i.e.    A --------» eth1 -------» network
         A --------» eth0 -------» computer B

However, connecting to Auto eth1 (eth1) and Auto eth0 (eth0) disconnects me from the network...

---

### Post by endotherm on 2010-09-30
ok, post this back for us:

```

sudo ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route

```

---

### Post by larry.said on 2010-09-30
Okay I think I figured it out.
The two connections had the same mask. I originally had eth1 as 10.1.6.10 and eth0 as 10.1.6.11. I changed eth0 to 10.2.6.11 and it now works.

Thanks for the help!

---

### Post by Iowan on 2010-10-01
That'd do it. It's not so much having the same mask (eg. 255.255.255.0) as having both interfaces in the same subnet (semantics). It plays havoc with routing... Glad you found it! 
(You can use Thread Tools to mark the thread solved.)

---


---
title: "multicast ubuntu 8.10 not working"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by whistlercanada on 2008-12-17
On my ubuntu 8.10, when tcpdump -i eth0 -p, and then run my application, I could see the request of joining the right multicast group ip/port send out from eth0. Then I see the multicast packets receiving there.

However my application that is supposed to receive and process these packets doesn't see anything. I searched some forum which suggests there might be a firewall issue. But I don't have firewall. Any idea?

Thank you.

```

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

$ sudo ethtool -i eth0
driver: e1000e
version: 0.3.3.3-k6
firmware-version: 5.6-2
bus-info: 0000:0a:00.0

$ uname -a
Linux s 2.6.27-7-server #1 SMP Tue Nov 4 20:16:57 UTC 2008 x86_64 GNU/Linux
```

---

### Post by damageboy on 2008-12-22
I think I'm having the same problem.
tcpdump / tshark shows the IGMP gorup membership and incoming packets...
However I cannot get my application to actually return from recvfrom()...

Any ideas anyone?

---

### Post by damageboy on 2008-12-22
OK, Solution found!

Sometime along the way, ubuntu turned on rp_filter on by default.

This "sin" is perfomed in: /etc/sysctl.d/10-network-security.conf
So... All you need to do is edit the file and change the two lines with rp_filter=1 into rp_filter=0.

Apply with sysctl -p

You may need to take the interfaces down/up or even reboot the machine (in case you can't take the interface down and then up).

Short answer is... After disabling the rp_filter... It works!

---

### Post by whistlercanada on 2008-12-23
Yes, this did the trick. Thanks.

---


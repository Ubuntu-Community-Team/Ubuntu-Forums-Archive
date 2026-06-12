---
title: "Something rare in the output of &quot;route -n&quot;"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by asm2545w on 2011-10-05
Hi guys,

I have just executed this command:

$ route -n

And I have showed something rare. This is the output:


$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1


eth1 is my wireless adapter and my subnet is 192.168.1 with submask 255.255.255.0, but how about this line:

169.254.0.0  0.0.0.0  255.255.0.0     U     1000  0      0 eth1

I don't know which device is in my intranet.

Any idea?

Thanks in advance

---

### Post by haqking on 2011-10-05
> **asm2545w said:**
> Hi guys,

I have just executed this command:

$ route -n

And I have showed something rare. This is the output:


$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1


eth1 is my wireless adapter and my subnet is 192.168.1 with submask 255.255.255.0, but how about this line:

169.254.0.0  0.0.0.0  255.255.0.0     U     1000  0      0 eth1

I don't know which device is in my intranet.

Any idea?

Thanks in advance

169.254.x.x is a link local non routable address, usually used when no configuration such as static or DHCP is present, sometimes known as a APIPA or AVAHI address also

---

### Post by asm2545w on 2011-10-05
Thanks for the answer.

---


---
title: "How to use the second ip address?"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by enieffak on 2013-01-25
Hi

I've rented an "OpenVZ" server with two IP addresses.
In the OpenVZ control panel one can choose which of those two addresses should be the standard address.

At the moment it is possible to ping the standard address from the outside, but there's no reaction when pinging the second address.

I'd like to run two Tor bridge instances on this system.
Each bridge should have its own address. There seems to be an option in the torrc configuration file called "OutboundBindAddress [IP-Address]" for this.


> root@server2:~# ifconfig venet0:0
venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.30.33.abc  P-t-P:192.30.33.abc  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

root@server2:~# ifconfig venet0:1
venet0:1  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.30.33.def  P-t-P:192.30.33.def  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


(I replaced the last parts of the actual addresses for posting it here)

How do I get programs to use the second ip address? What can I do to achieve that ping requests get answered?

Thank you for your help.

---

### Post by enieffak on 2013-01-26
> root@server2:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 venet0


Any hints?

---

### Post by sudodus on 2013-01-26
Can you ping the second ip address from the inside?

And are the MAC addresses different (or the same)? You have all zeros there.

---

### Post by enieffak on 2013-01-26
> **sudodus said:**
> Can you ping the second ip address from the inside?

And are the MAC addresses different (or the same)? You have all zeros there.

Thanks for your help!

I think the MAC addresses are ale blank because the devices are virtual devices.

I was able to ping the second ip address from the inside.

Just contacted my server provider minutes ago and it was their fault:

"The IP had been nullrouted before but I didn't successfully mark it off the available IP list. I gave you a new one anyway."


So it does work now.

---

### Post by sudodus on 2013-01-26
I'm glad it works :KS

Time for kaffeine :-)

---


---
title: "Need help with kvpnc and routing"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by trundlenut on 2009-09-25
I have installed kvpnc and I can connect via pptp to my work network successfully _but_ I can't fathom out how to get the routing working.

I am assigned an IP from the work network but I can't access anything inside the network.

Here is the output from route:

```
simon@black-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.49.XXX.XXX    192.168.1.254   255.255.255.255 UGH   0      0        0 eth1
192.168.0.17    *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```

Any ideas on what I'm doing wrong?

---

### Post by trundlenut on 2009-09-26
bumpty bump

---

### Post by provomike on 2009-10-09
sooooo - did you get this answered? If so, what was the fix. I find myself in the same boat.

---

### Post by t0mppa on 2009-10-09
> **trundlenut said:**
> I am assigned an IP from the work network but I can't access anything inside the network.

Here is the output from route:

```
simon@black-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
62.49.XXX.XXX    192.168.1.254   255.255.255.255 UGH   0      0        0 eth1
192.168.0.17    *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```

Any ideas on what I'm doing wrong?

Well, taking the original post as an example, the problem is the following:

The routing table shows the possible choices for connections are:
[LIST]
[*]to 64.49.xx.xx (mask shows it's only one IP) through 192.168.1.254 on eth1
[*]to 192.168.0.17 (single IP again) directly on ppp0
[*]to 192.168.1.y (subnet where y can be anything between 0 and 255) directly on eth1
[*]every other address goes through the default gateway on eth1
[/LIST]
And naturally, getting to say 192.168.0.1 through the default gateway is not going to work.

So, assuming the need to authenticate through a certain computer to gain access to the private network, the solution is to create a route to 192.168.0.0 with 192.168.0.17 as the gateway and 255.255.255.0 as the mask and ppp0 as the interface.

---

### Post by trundlenut on 2009-10-10
I'd forgotten about this thread.  I realised it was me being a bit thick, I was trying to set the route to the remote network by using an ip of 192.168.0.1 and a netmask of 255.255.255.255 when I should have used an ip of 192.168.0.0 with that mask, when I changed it to the latter it worked fine.

---


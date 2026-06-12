---
title: "How to specify which NIC to use for which service?"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by Subbeh on 2013-07-02
Hi,

I'm running Ubuntu 12.04 LTS on a system with a wired network adapter (eth0) and a wireless adapter (wlan0). Both these adapters are connected to a different network with internet access.
Is it possible to use wlan0 for internet browsing for example, and to run an apache webserver on the eth0 adapter?

---

### Post by TheFu on 2013-07-02
Having 2 network connections is an advanced topic and requires more than a fundamental understanding of internet routing.  Only 1 of the connections can have the "default route" to the internet.  Sure, there are ways to tunnel connections and do unbelievably complex stuff, but usually, it is just easier to set the priority using the routing Metric for each interface or just disable the slower one.

If the web server only needs to be accessible on the internal network, it can be handled.

If both interfaces need to communicate with the internet, it becomes a non-trivial problem.  Or you can setup a reverse proxy server on the specific subnet you want all web traffic to go over and force it to only use the wired connection on your web server.  

If you provide more specifics about the networks ... IPs, subnets, netmasks, and routing, someone might be able to help more.  I don’t think the public IPs matter, so don't provide those.  This route table might help.
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 virbr1
192.168.1.0     *               255.255.255.0   U     0      0        0 or0
172.20.1.0      *               255.255.255.0   U     0      0        0 bus0
10.1.1.0        *               255.255.255.0   U     0      0        0 virbr0
default         rt1             0.0.0.0         UG    1      0        0 or0
```

---

### Post by Subbeh on 2013-07-05
Thanks for the reply TheFu. I think the easiest option for me is actually to create a virtual machine and use one of the two network interfaces for it.

---

### Post by TheFu on 2013-07-05
> **Subbeh said:**
> Thanks for the reply TheFu. I think the easiest option for me is actually to create a virtual machine and use one of the two network interfaces for it.

Or you can use ifup and ifdown scripts to bring the specific interface you want working up/down.
The VM idea should work too, provided you remember to enable/disable the specific NIC from the VM-settings side of the host machine.

Or you could create a tunnel for specific traffic using **iptables** and the **-m owner --uid-owner** options. I've not tried this myself and it may not work. Some careful reading will be necessary.

Or I could be misunderstanding what you hope to accomplish completely.

---


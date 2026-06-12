---
title: "Can't ssh to vmware guest"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by herda05 on 2010-03-22
All,

I'm running Ubuntu 9.1 i386 in test with Vmware 2.0.2. I used [Radu Cotescu's patch and instructions]("http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/") to get vmware installed. Everything seems to be running fine in the guest machine (CentOS 5), except I can't ssh from the Ubuntu host to the guest machine.

This guest is a clone of one that is running under on my Ubuntu 8.1 host and networking is fine there. I'm wondering if there were changes to routing or bridging in Ubuntu 9.1 to cause this. I've been digging through google for a while, but haven't seen others reporting any issues. This is definitely particular to Karmic Koala though.

The host's routing table is:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     0      0        0 vmnet3
192.168.190.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.235.0   *               255.255.255.0   U     0      0        0 vmnet1
link-local   *               255.255.0.0   U     0      0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0   0 wlan0
```

The guest's routing table is:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
169.254.0.0     *               255.255.255.0   U     0      0        0 eth0
default   192.168.0.2               255.255.255.0   UG     0      0        0 eth0
```

My routing table on the Ubuntu 8.1 host differs by the link-local line only, and the guests are exactly the same.

I can ssh from the guest into the host, as 192.168.0.2 is the hosts ip on the vm network. The host *should* be able to ssh to the guest as it does in Ubuntu 8.1.

Does anyone know enough about the vmware networking setup to point me in the direction of what might be the problem?

thanks,
Dan H.

---

### Post by johnson.d on 2010-03-22
You can have the following checks:

1) Check the firewall settings in the guest. Try disabling firewall and check whether you can ssh from the host.

2) Check TCP wrappers settings like host.deny and host.allow files in the guest.

---

### Post by herda05 on 2010-03-22
There is no firwall running on the guest.

Both files are empty, and tcp wrappers is not enabled.

On the host, unless Ubuntu 9.1 is enabling something by default that it wasn't in 8.1 I'm not sure if there is a firwall there. I can ssh from my 9.1 machine to my 8.1 machine.

I noticed something interesting in test. If the guest is using bridged networking (yeah wireless bridging!), I can access it. Problem is I'd like this guest to be part of an AD test domain I've setup and I need it to at least be nat'd. Otherwise I'll have two AD's on the same network duking it out.

---


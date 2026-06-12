---
title: "network routing issue"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by ceverett on 2011-02-27
I need to connect to the admin web site on my Brother HL-2170 printer.  It's configuration output page claims that its IP address is 169.254.154.59 net mask 255.255.0.0, configured via APIPA.

My laptop is using WICD.  I can't seem to configure WICD to use a network address like 169.254.154.10, it just tries and dies.

So then I turned to the command line.

```

sudo ifconfig eth0:1 169.254.154.59 netmask 255.255.0.0 broadcast 169.254.255.255
sudo route add -net 169.254.0.0 netmask 255.255.0.0 eth0

```

That gives me a configuration like this:

```


ceverett@johannes:/var/log$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:15:c5:16:70:15  
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe16:7015/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78484889 (78.4 MB)  TX bytes:10564269 (10.5 MB)
          Interrupt:17 

ceverett@johannes:/var/log$ ifconfig eth0:1 
eth0:1    Link encap:Ethernet  HWaddr 00:15:c5:16:70:15  
          inet addr:169.254.0.10  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

ceverett@johannes:/var/log$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

I get "destination host unreachable" when I try to ping the printers supposed IP address.  Is there something I'm doing obviously wrong?

---

### Post by dmizer on 2011-02-28
> **ceverett said:**
> I need to connect to the admin web site on my Brother HL-2170 printer.  It's configuration output page claims that its IP address is 169.254.154.59 net mask 255.255.0.0, configured via APIPA.

You can't reach a 169.254.x.x address. This address means that your printer is not connected to any network at all. If it was connected to your network, it would have a 192.168.1.x address.

More information here: [http://en.wikipedia.org/wiki/Link-local_address](http://en.wikipedia.org/wiki/Link-local_address)

It looks like you will need to use the printers menu to manually configure it to connect to your network.

---

### Post by mazato on 2011-02-28
I think what you did was just  print the configuration page of your printer and got that IP address from that paper. I think your printer is not getting an IP address by the DHCP server on your router or gateway thus the printer is using an APIPA (private) address, if already connected to your LAN. Is it connected to your LAN already?... 
You need to connect your printer to your LAN somehow. Did you check your printer's manual first?!

Good luck!!

---

### Post by ceverett on 2011-02-28
The cable and switch port are known good, I swapped cables with this laptop.  Previously, the thing had a fixed IP address at 192.168.1.10.  My troubles began when I switched out toner cartridges; at some point I did a factory reconfiguration on the printer.

I guess this implies that the network port on the printer has gone bad.  Crud.

---


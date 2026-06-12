---
title: "Multiple NIC Routing? Problem"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by einstein on 2010-09-09
I think I know what the problem is but I cannot figure out how to fix it properly....
I have a server with eth0, eth1 and wlan0:[LIST=1]
[*]eth0 is connected to the Internet via a router w/dhcp server followed by DSL modem
[*]eth1 is connected to a wireless access point also with dhcp server (different subnet)
[*]wlan0 is there "just kuz", is connected to the router is not supposed to do anthing particularly useful
[/LIST]
After booting or restarting networking, the Internet is inaccessible and the web server cannot be accessed.  I can connect by SSH using IP address of server.
Everythin works again if I;
[LIST=1]
[*]dhclient -r eth1 and wlan0, OR,
[*]dhclient -r eth0 and then dhclient eth0.
[/LIST] 
It appears that eth0 needs to be configured last (so that resolv.conf does not point to a useless AP gateway) but I cannot figure out how to do this.  More correctly, I suspect, my routing tables need tweaking but I have no idea how to do this.
Can someone offer some advice or point me to a suitable how to?
Thanks in advance.
Best regards,

---

### Post by dmizer on 2010-09-09
> **einstein said:**
> [LIST=1]
[*]eth0 is connected to the Internet via a router w/dhcp server followed by DSL modem [COLOR="Red"](ok)[/COLOR]
[*]eth1 is connected to a wireless access point also with dhcp server (different subnet) [COLOR="Red"](ok)[/COLOR]
[*]wlan0 is there "just kuz", is connected to the router is not supposed to do anthing particularly useful [COLOR="Red"](not ok)[/COLOR]
[/LIST]


Without looking at your ifconfig output I can't be sure, but I believe your problem is that both eth0 and wlan0 are connected to the same router and are on the same subnet. This confuses both the router and Ubuntu. You can use one or the other, but not both.

Edit:
For more troubleshooting, please post the following information
```
ifconfig
```
```
route
```

---

### Post by einstein on 2010-09-09
> **dmizer said:**
> Without looking at your ifconfig output I can't be sure, but I believe your problem is that both eth0 and wlan0 are connected to the same router and are on the same subnet. This confuses both the router and Ubuntu. You can use one or the other, but not both.

Edit:
For more troubleshooting, please post the following information
Here it is.  I have removed wlan0 as you suggested.  All network connectivity seemed to be in order when I obtained the following.  So, no two nics on the same subnet?
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:02:b3:0a:14:7d  
          inet addr:192.168.1.184  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe0a:147d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10873842 (10.8 MB)  TX bytes:14109766 (14.1 MB)

eth1      Link encap:Ethernet  HWaddr 00:a1:b0:01:17:36  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:134059 (134.0 KB)  TX bytes:123651 (123.6 KB)
          Interrupt:9 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:820818 (820.8 KB)  TX bytes:820818 (820.8 KB)

```
route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by dmizer on 2010-09-09
> **einstein said:**
> So, no two nics on the same subnet?

Not without some fancy network configurations which you most probably have no need for. Your best bet is simply to leave the wlan0 adapter unconfigured as it really does nothing anyway.

---


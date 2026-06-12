---
title: "Wireless connected, but no internet?"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by avspavan on 2008-12-16
Hi all:

I have a wireless internet problem. My laptop has Ubuntu 8.10. It was working all fine till I had installed firewall (lokkit) today morning. The internet doesnot work anymore. I have uninstalled lokkit. My network manager shows all available wireless networks around, and says it is connected to the wireless at my home. But I am not able to surf any webpage. It says address not found. I think it is because of firewall install/uninstall. Can you suggest how to go about solving this?? 

Thanks
Pavan

---

### Post by cdtech on 2008-12-16
Can you ping using the command line?

What is the output of:
```
ifconfig -a
```
and:
```
route -n
```

---

### Post by avspavan on 2008-12-16
> **cdtech said:**
> Can you ping using the command line?

What is the output of:
```
ifconfig -a
```
and:
```
route -n
```

Hi:

Please see below the output:

pavan@neone:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:23:f8:e2:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr e6:d2:3e:e1:c9:6d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:60:b3:b6:79  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:feb3:b679/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59379 (59.3 KB)  TX bytes:1713 (1.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-60-B3-B6-79-36-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pavan@neone:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

THanks
Pavan

---

### Post by avspavan on 2008-12-16
Hi:

I had forgotten to mention that neither Ethernet nor wireless work now. It shows connected for ethernet connection too...but when I try to surf the net, firefox says address not found..even the ping doesn't work. I pinged 64.233.167.99..it says operation not permitted

any help?
Pavan

---

### Post by cdtech on 2008-12-16
You should put the outputs into "code blocks" so it's human readable. Sorry I went to sleep. Try running "sudo ufw disable && sudo ufw enable" to reset the firewall.

---

### Post by avspavan on 2008-12-16
> **cdtech said:**
> You should put the outputs into "code blocks" so it's human readable. Sorry I went to sleep. Try running "sudo ufw disable && sudo ufw enable" to reset the firewall.

Hi:

Thanks a million! This works. I don't understand what is this ufw? I had installed only lokkit..and uninstalled it. But only after "sudo ufw disable" my internet is working. Should I always keep this disabled? 

Thanks again! you made my day!
Pavan

---


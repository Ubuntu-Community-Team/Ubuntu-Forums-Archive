---
title: "ubuntu home network"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by xzx1kf on 2009-08-01
Hi,

I have two laptops running xubuntu. My problem is that I can't share files between them using nfs. Further on to that I can't even ping either laptop from the other. I just get a "Destination Host Unreachable" error. Which I assume is causing the problem with the file sharing. 

I have scoured the Internet for a resolution but to no avail. I am a network newbie. 

ifconfig on both machines is pretty similar, just the ip and hw addresses differ:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:00:67:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:65:c5:45  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe65:c545/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4932 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4355956 (4.3 MB)  TX bytes:861359 (861.3 KB)
          Interrupt:17 Base address:0x6000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37000 (37.0 KB)  TX bytes:37000 (37.0 KB)

can anybody offer me any help?

Thanks

---

### Post by jason31 on 2009-08-01
Just so you know Im not a linux expert, but I have done alot of work with windows networks.

iIf your using DHCP, renew it on each machine

(This might be a windows thing only) Make sure that both machines are on the same workgroup

And personally I would say that sounds like a firewall or some other badly configured software iissue. Check your firewall, sometimes people have their firewall in  a complete lockdown mode, even on their home network. Thats fine on public wifi, but at home it doesnt need that much security.

---

### Post by xzx1kf on 2009-08-01
Thanks. I've checked out the firewall issue, and I'm pretty sure that's not it, iptables -L lists not blocked connections, and firestarter doesn't even list an attempted connection when I try to ping from the other laptop.

ping does seem to recognise the hostname of the other laptop as it resolves the hostname to an ip address. So I don't understand why it doesn't work.

just ask if any other info is required and i'll post it. 

its doing my head in now though. Could it be something to do with my wireless router? I know i've been able to share through windows before over the same network, so why not linux???

Thanks

---

### Post by eldragon on 2009-08-01
please post the outcome of the following commands on both computers
```

$ ifconfig -a
$ route
$ iptables -L

```


can they connect to the internet?

---

### Post by xzx1kf on 2009-08-01
Laptop 1

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         api.home        0.0.0.0         UG    0      0        0 eth1


sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:c5:00:67:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:65:c5:45  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe65:c545/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:253299 (253.2 KB)  TX bytes:63377 (63.3 KB)
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6504 (6.5 KB)  TX bytes:6504 (6.5 KB)

pan0      Link encap:Ethernet  HWaddr 42:f4:72:95:8c:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Laptop 2

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:4a:09:3f:a6
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:3 Base address:0x9000

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:142 errors:0 dropped:0 overruns:0 frame:0
         TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:12620 (12.6 KB)  TX bytes:12620 (12.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:2a:81:91
         inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
         inet6 addr: fe80::211:50ff:fe2a:8191/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:71 errors:0 dropped:0 overruns:0 frame:0
         TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:7918 (7.9 KB)  TX bytes:19399 (19.3 KB)
         Interrupt:4 Memory:34000000-34080000

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         api.home        0.0.0.0         UG    0      0        0 wlan0

sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by eldragon on 2009-08-01
can you ping the other computer's ip?

can you ping the router's ip?

if you can ping the router's ip but not the other computer's ip, then check your router's configuration, it might be isolating the wireless hosts from your lan.

if you can ping each other through their ips, then try accessing their shares through their ip instead of their names

---

### Post by xzx1kf on 2009-08-01
I can ping the router from both. Both can connect to the Internet. What sort of router setting would I be looking out for? Can't ping the other laptop by ip though

---

### Post by eldragon on 2009-08-01
> **xzx1kf said:**
> I can ping the router from both. Both can connect to the Internet. What sort of router setting would I be looking out for? Can't ping the other laptop by ip though

check the wireless lan security settings, access restrinctions, etcetera, i wouldnt know for sure, each router has its own way of isolating the wireless hosts. for a quick test, plug both laptops with an ethernet cable to the router switch, and check if they can ping each other this way

---

### Post by xzx1kf on 2009-08-02
solved it... but i don't know why. I just reset my router to the default settings. Not that I had ever changed them anyway!

Thanks for your help.

---


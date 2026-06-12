---
title: "Network Manager-i can't give ip to my NIC"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by ravinambrayil on 2010-02-18
hi,
i am having a problem with my network. I am using Ubuntu 9.10 in my HP 510 notebook. i cannot give IP manually, to my NIC. when i left click Network manager, it shows Wired Network (Intel Pro/100VE), device is not managed. Both wired & wireless have shown like this. And also I have problem with conneting to internet (DSL). I have to run 'pppoeconf' tool everytime when i need to connect internet. i have to run pppoeconf many times untill I can browse.When i used ubuntu 8.10, i have no problem with that. 
Can you please help me to solve this problem. 

RAVI

---

### Post by Iowan on 2010-02-18
Do you have definitions for interfaces (other than "lo") in */etc/network/interfaces*

---

### Post by ravinambrayil on 2010-02-22
> **Iowan said:**
> Do you have definitions for interfaces (other than "lo") in */etc/network/interfaces*


hi,
the file /etc/network.interfaces details are here
"
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet dhcp
~                                                                               
~                        
"


The problem is when i used ubuntu 9.10 live cd (Booted from live cd), i have no problem with network manager. I can give ip  using network manager, it was shown as auto eth0 in network manager.
After i installed ubuntu, i can't give ip manually using network manager. ethernet is shown as ifupdown (eth0), & edit option is not active. Also it isnot taking Ip from dhcp (Modem)

I installed package "network" & configured ethernet to dhcp using newly installed "network" package. then i did run the command ifconfig, the output is like this....
(dhcp pool is 192.168.1.2 -192.168.1.254)
eth0      Link encap:Ethernet  HWaddr 00:16:d4:e9:16:46  
          inet6 addr: fe80::216:d4ff:fee9:1646/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:275014642 (275.0 MB)  TX bytes:8376263 (8.3 MB)

ravi@ravi-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:e9:16:46  
          inet6 addr: fe80::216:d4ff:fee9:1646/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:275014642 (275.0 MB)  TX bytes:8376263 (8.3 MB)

eth1      Link encap:Ethernet  HWaddr 00:16:6f:ca:97:c4  
          inet6 addr: fe80::216:6fff:feca:97c4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:84 (84.0 B)
          Interrupt:21 Base address:0xc000 Memory:d0000000-d0000fff 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:d4:e9:16:46  
          inet addr:169.254.7.48  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)




I need ur help ....please........

---

### Post by Iowan on 2010-02-22
I guess I'm not familiar with the "network" package. The definition of eth0 in */etc/network/interfaces* may have blocked NM from managing/setting the IP address. You could edit the file, and "comment out" the definition for eth0:```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

#auto eth0
#iface eth0 inet dhcp
```Restart or reboot (I prefer reboot to get NM and networking back in sync), and you *should* then be able to configure eth0 through NM. (It may not work - since the dsl interface uses eth0...)

---


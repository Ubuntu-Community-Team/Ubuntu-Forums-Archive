---
title: "iptables rate limiting for bridged connection  (kvm created bridge)"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2010-10-27
I have a bridged network setup ifconfig -a 
gives following output

```
br0       Link encap:Ethernet  HWaddr 00:26:b9:82:42:38  
          inet addr:192.168.1.1  Bcast:192.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe82:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109293717 (109.2 MB)  TX bytes:13045804 (13.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:26:b9:82:42:34  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:36 Memory:d6000000-d6012800 

eth1      Link encap:Ethernet  HWaddr 00:26:b9:82:42:36  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 Memory:d8000000-d8012800 

eth2      Link encap:Ethernet  HWaddr 00:26:b9:82:42:38  
          inet6 addr: fe80::226:b9ff:fe82:4238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106427544 (106.4 MB)  TX bytes:13644205 (13.6 MB)
          Interrupt:32 Memory:da000000-da012800 

eth3      Link encap:Ethernet  HWaddr 00:26:b9:82:42:3a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:426584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106667150 (106.6 MB)  TX bytes:106667150 (106.6 MB)

vnet0     Link encap:Ethernet  HWaddr 12:7f:c9:1b:4b:55  
          inet6 addr: fe80::107f:c9ff:fe1b:4b55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4919136 (4.9 MB)  TX bytes:102875453 (102.8 MB)

vnet1     Link encap:Ethernet  HWaddr 26:c0:8d:f2:14:29  
          inet6 addr: fe80::24c0:8dff:fef2:1429/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2911695 (2.9 MB)  TX bytes:102792920 (102.7 MB)

vnet2     Link encap:Ethernet  HWaddr 3e:0d:34:3e:24:3f  
          inet6 addr: fe80::3c0d:34ff:fe3e:243f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:144288 (144.2 KB)  TX bytes:102302055 (102.3 MB)

vnet3     Link encap:Ethernet  HWaddr 6e:13:93:c4:44:49  
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:426584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106667150 (106.6 MB)  TX bytes:106667150 (106.6 MB)

vnet0     Link encap:Ethernet  HWaddr 12:7f:c9:1b:4b:55  
          inet6 addr: fe80::107f:c9ff:fe1b:4b55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4919136 (4.9 MB)  TX bytes:102875453 (102.8 MB)

vnet1     Link encap:Ethernet  HWaddr 26:c0:8d:f2:14:29  
          inet6 addr: fe80::24c0:8dff:fef2:1429/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2911695 (2.9 MB)  TX bytes:102792920 (102.7 MB)

vnet2     Link encap:Ethernet  HWaddr 3e:0d:34:3e:24:3f  
          inet6 addr: fe80::3c0d:34ff:fe3e:243f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:144288 (144.2 KB)  TX bytes:102302055 (102.3 MB)

vnet3     Link encap:Ethernet  HWaddr 6e:13:93:c4:44:49  
          inet6 addr: fe80::6c13:93ff:fec4:4449/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:90625 (90.6 KB)  TX bytes:102221778 (102.2 MB)

```
I am not sure of following things

1) When limiting rate of incoming connections what should I specify interface following rule definitely will not work

-A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --update --seconds 90 --hitcount 5 --name DEFAULT --rsource -j DROP
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -m state --state NEW -m recent --set --name DEFAULT --rsource

2) For setting up other IPTABLE rules if I do not specify the interface will that work 
Some thing of following sort
-A INPUT -s 218.38.18.159/32 -p tcp -m tcp --dport 22 -j DROP

3) What are these vmnet1,vmnet2,vmnet3,vmne4 which I see above. I used kvm and virt-manager to create a bridged setup.

---


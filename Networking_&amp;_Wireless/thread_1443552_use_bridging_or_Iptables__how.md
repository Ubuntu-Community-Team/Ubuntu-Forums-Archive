---
title: "use bridging or Iptables?  how?"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by sinusoid on 2010-03-31
Hi everyone.  Thanks for looking at this.  

I am trying to figure the following out:

Basically, I have a windows 2003 serv virtual machine (vmware) inside Ubuntu 9.10.   

The Ubuntu machine has IFconfig:

```

sam@sam-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b8:c8:8b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:16:cf:80:e1:73  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe80:e173(slash)64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76734 errors:0 dropped:0 overruns:0 frame:4709
          TX packets:68133 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57927053 (57.9 MB)  TX bytes:13361129 (13.3 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1(slash)128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12988 (12.9 KB)  TX bytes:12988 (12.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.242.1  Bcast:172.16.242.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1(slash)64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.206.1  Bcast:172.16.206.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8(slash)64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Iptables is 

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
           all  --  anywhere             10.1.10.0 (slash 25)

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    


``````

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.242.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
10.1.10.0       0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.206.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```Also ran a "sudo iptables -t nat -L"

```
 
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   


```
And here is some of the tcpdump, so I am assuming my packets/routes are correct from the wireless router:

```


17:14:51.873292 IP Laurie.home > 10.1.10.1: ICMP echo request, id 768, seq 33811, length 40
17:14:52.384680 IP 169.254.1.175.37679 > 169.254.1.255.5000: UDP, length 12
17:14:52.384949 IP Laurie.home > 172.16.206.128: ICMP echo request, id 768, seq 34067, length 40
17:14:52.804170 IP sam-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.255.in-addr.arpa. (46)
17:14:52.860359 IP sam-laptop.home.59642 > iad04s01-in-f147.1e100.net.www: Flags [F.], seq 1, ack 1, win 108, options [nop,nop,TS val 1512845 ecr 2621050801], length 0
17:14:52.860430 IP sam-laptop.home.39915 > iad04s01-in-f104.1e100.net.www: Flags [F.], seq 1, ack 1, win 558, options [nop,nop,TS val 1512845 ecr 2621054269], length 0


```
The internal 2003 serv (I know, i know)  has ips of 172.16.206.128 and 10.1.10.1 on the 255.255.255.0 subs.

I am curious ---- why can't I ping or simply access the internal server on my ubuntu machine from a another computer on the 192.168.1.0(slash)25 physcial network?

Do I need a bridge?  Iptables?  Can they both do the same thing?
How might I implement?   I have done a lot of searching but really not found the exact answer and the man pages aren't helping me too much...

THANKS!!!!!

---

### Post by DGortze380 on 2010-03-31
> **sinusoid said:**
> Hi everyone.  Thanks for looking at this.  

I am trying to figure the following out:

Basically, I have a windows 2003 serv virtual machine (vmware) inside Ubuntu 9.10.   

The Ubuntu machine has IFconfig:

```

sam@sam-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b8:c8:8b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:16:cf:80:e1:73  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe80:e173(slash)64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76734 errors:0 dropped:0 overruns:0 frame:4709
          TX packets:68133 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57927053 (57.9 MB)  TX bytes:13361129 (13.3 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1(slash)128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12988 (12.9 KB)  TX bytes:12988 (12.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.242.1  Bcast:172.16.242.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1(slash)64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.206.1  Bcast:172.16.206.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8(slash)64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Iptables is 

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
           all  --  anywhere             10.1.10.0 (slash 25)

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    


``````

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.242.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
10.1.10.0       0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.206.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```Also ran a "sudo iptables -t nat -L"

```
 
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   


```
And here is some of the tcpdump, so I am assuming my packets/routes are correct from the wireless router:

```


17:14:51.873292 IP Laurie.home > 10.1.10.1: ICMP echo request, id 768, seq 33811, length 40
17:14:52.384680 IP 169.254.1.175.37679 > 169.254.1.255.5000: UDP, length 12
17:14:52.384949 IP Laurie.home > 172.16.206.128: ICMP echo request, id 768, seq 34067, length 40
17:14:52.804170 IP sam-laptop.home.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.255.in-addr.arpa. (46)
17:14:52.860359 IP sam-laptop.home.59642 > iad04s01-in-f147.1e100.net.www: Flags [F.], seq 1, ack 1, win 108, options [nop,nop,TS val 1512845 ecr 2621050801], length 0
17:14:52.860430 IP sam-laptop.home.39915 > iad04s01-in-f104.1e100.net.www: Flags [F.], seq 1, ack 1, win 558, options [nop,nop,TS val 1512845 ecr 2621054269], length 0


```
The internal 2003 serv (I know, i know)  has ips of 172.16.206.128 and 10.1.10.1 on the 255.255.255.0 subs.

I am curious ---- why can't I ping or simply access the internal server on my ubuntu machine from a another computer on the 192.168.1.0(slash)25 physcial network?

Do I need a bridge?  Iptables?  Can they both do the same thing?
How might I implement?   I have done a lot of searching but really not found the exact answer and the man pages aren't helping me too much...

THANKS!!!!!

Change your virtual machines adapter to bridged. It will get an IP from your router that you can use on your LAN machine to access the VM.

---


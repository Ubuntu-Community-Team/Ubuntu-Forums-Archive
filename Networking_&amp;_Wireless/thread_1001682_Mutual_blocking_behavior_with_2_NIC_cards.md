---
title: "Mutual blocking behavior with 2 NIC cards"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by EdMartin on 2008-12-04
I'm running 8.10 desktop. As far as I can tell, this problem started after a recent kernel upgrade.

My office desktop computer has two NIC cards, one (eth0) with a static IP address on a public-facing network that connects to the internet via a Cisco router at our end of a T1 line and the other (eth1) with a dynamic, DHCP-provided IP address on the office LAN. (The office LAN has a D-Link router that provides internet access for the LAN. So the D-Link router, like my desktop machine, has a LAN address and an address on the public-facing network that gets out to the internet via the Cisco router and the T1.)

The reason for my desktop machine's public IP address is so that I can gain access via SSH with an NX Client on my laptop and work on my office computer while at home.

The problem is that, following one of the recent kernel upgrades, I can no longer access the internet from the office computer when BOTH cards are enabled. Disable either one of them and internet access is restored.

Does anyone have any idea what's causing this behavior and how to fix it? And why should this behavior have started when I upgraded the kernel?

Any and all help will be greatly appreciated.

Ed

---

### Post by EdMartin on 2008-12-04
Even more troubling!

The behavior is intermittent.

With both cards enabled and without changing any settings, I could access the internet from my desktop machine all morning. Now, all of a sudden, after leaving it inactive for an hour or so, I can't.

It never used to behave like this under 8.04, nor right after I upgraded to 8.10. So what is it about the recent kernel upgrades that is causing this annoying flakiness?

Ed

---

### Post by IQRules on 2008-12-04
After reboot, both NIC work just fine?
Is it DHCP or static ip? Post your /etc/network/interfaces and route.
I doubt it is related to kernel upgrade. More like standby or hibernate issue to me.

---

### Post by EdMartin on 2008-12-04
/etc/network/interfaces:
```

auto lo
iface lo inet loopback

# LAN NIC card
auto eth0
iface eth0 inet dhcp
	pre-up iptables-restore < /etc/iptables.up.rules

# Public NIC card
iface eth1 inet static
	address xxx.xxx.xxx.20
	netmask 255.255.255.224
	gateway xxx.xxx.xxx.1
auto eth1

```

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.0   0.0.0.0         255.255.255.224 U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         xxx.xxx.xxx.1   0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

And just for the heck of it, iptables -L:
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:ACK/ACK 
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state RELATED 
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain dpts:1024:65535 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:auth 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Thanks for any insight you can provide.

Ed

---

### Post by EdMartin on 2008-12-05
In answer to your question about whether both NIC cards work after a reboot: Sometimes yes, sometimes no.

In order to investigate whether suspending and/or hibernating are playing a role, I have disabled both by commenting out

```

ACPI_SLEEP=true
ACPI_HIBERNATE=true

```

in /etc/default/acpi-support and rebooting. It makes no difference to the sometimes-on-sometimes-off behavior I'm experiencing with both NIC cards enabled.

I have discovered, however, that if it happens that I have both cards enabled, and there is no internet connection, then I can consistently reacquire internet connectivity by executing

```

sudo ifdown eth1
sudo ifup eth1
sudo /etc/init.d/networking restart

```

Oddly, throughout all this experimentation (with the exception of when I have deliberately disabled one of the cards) ifconfig consistently reports something similar to

```

eth0      Link encap:Ethernet  HWaddr 00:a0:c9:9c:38:35  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6782354 (6.7 MB)  TX bytes:1845005 (1.8 MB)

eth1      Link encap:Ethernet  HWaddr 00:11:43:9f:1c:7b  
          inet addr:xxx.xxx.xxx.20  Bcast:xxx.xxx.xxx.31  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6147633 (6.1 MB)  TX bytes:463957 (463.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:428 (428.0 B)  TX bytes:428 (428.0 B)

```

regardless of whether I have internet connectivity.

Bit of a puzzler, eh?

Ed

---

### Post by EdMartin on 2008-12-11
I appear to have solved the problem.

It did it by assigning static IPs to both cards and by only specifying a gateway for the public-facing NIC card in /etc/network/interfaces.

As a result, "route -n" now yields

```

Destination   Gateway       Genmask         Flags Metric Ref Use Iface
xxx.xxx.xxx.0 0.0.0.0       255.255.255.224 U     0      0   0   eth1
192.168.1.0   0.0.0.0       255.255.255.0   U     0      0   0   eth0
169.254.0.0   0.0.0.0       255.255.0.0     U     1000   0   0   eth1
0.0.0.0       xxx.xxx.xxx.1 0.0.0.0         UG    100    0   0   eth1

```

Everything now seems to be hunky-dory with ready internet access while both NIC cards are enabled (as well as when the LAN card is disabled).

Ed

---


---
title: "can't access internet through ethernet"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by jmmmp on 2008-12-21
Hi,

on my desktop I can't access the internet, although everything seems to be fine with the ethernet board. I also have XP on the same machine, and it works without problems.

What's weird is that I can also see my laptop on the windows network through samba, and also access it. But not the internet.

The ubuntu on my desktop is totally clean, since I never had internet on it I couldn't make any updates etc.

Here's the result of a ifconfig -a:

eth0      Link encap:Ethernet  Hardware Adresse 00:1c:25:cb:11:02  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:25ff:fecb:1102/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metrik:1
          RX packets:75 errors:4 dropped:0 overruns:0 frame:4
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:13108 (12.8 KB)  TX bytes:5352 (5.2 KB)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1047 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:52876 (51.6 KB)  TX bytes:52876 (51.6 KB)

---

### Post by Iowan on 2008-12-21
What is result of **route**?
IP address is via DHCP?
What provides IP address?

---

### Post by jmmmp on 2008-12-21
Ip adresses at home are provided by the router (through dhcp, I guess). They're always automatic.

The result from route -v is 

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface


Strange, now I can't access the share anymore (rebooted both computers). But the result of ifconfig -a seems to be the same.

---

### Post by albinootje on 2008-12-21
> **jmmmp said:**
> Ip adresses at home are provided by the router (through dhcp, I guess). They're always automatic.

The result from route -v is 

Please make that :
```

route -n
cat /etc/resolv.conf

```
Is your Ubuntu machine connected to a switch or to another machine, or directly to a DSL-router or cable-modem ?

---

### Post by Iowan on 2008-12-21
I'm wondering if the gateway setting is missing.  **dhclient** *should* be requesting it.

---

### Post by jmmmp on 2008-12-22
Hi,

here are the results of the commands. All computers in the house are connected to a router, which is connected to the dsl modem. All other computers/systems (including ubuntu on my laptop and windows on the desktop) work without problems:

route -n

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface

cat /etc/resolv.conf

nameserver 192.168.1.1


and again, ifconfig (just in case)

eth0      Link encap:Ethernet  Hardware Adresse 00:1c:25:cb:11:02  
          inet6-Adresse: fe80::21c:25ff:fecb:1102/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:4568 (4.4 KB)  TX bytes:492 (492.0 B)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1476 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:73800 (72.0 KB)  TX bytes:73800 (72.0 KB)

---

### Post by jonobr on 2008-12-22
Hello

Your last post is different to your first

On the first ifconfig you had an ip address for the eth0 
192.168.1.2

On the second its empty

I recommend open a terminal and do the following

sudo ifconfig eth0 down
sudo ifconfig eth0 up

This will bounce your ethernet connection.
let us know if you then get a 192 IP address after doing that

NOTE-: this should be done on the local machine and not across a network as you will loose connection when you do that

---

### Post by jmmmp on 2008-12-22
Hi,

quite strange. I just rebooted and the result is different now. Here is the output of the same commands, route -n, cat /etc/resolv.conf, ifconfig.

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


nameserver 192.168.1.1



eth0      Link encap:Ethernet  Hardware Adresse 00:1c:25:cb:11:02  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:25ff:fecb:1102/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metrik:1
          RX packets:15 errors:11 dropped:0 overruns:0 frame:11
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3070 (2.9 KB)  TX bytes:6900 (6.7 KB)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1542 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:77100 (75.2 KB)  TX bytes:77100 (75.2 KB)


And just in case, I did the ifconfig up / down afterwards. the result of route -n has only the first line of the above notated output.

---

### Post by Iowan on 2008-12-22
Well, it _looks_ better - still won't access internet?

---

### Post by jmmmp on 2008-12-22
No. actually, that was the result by step 1, I think.

The strange is that if I do Ubuntu's network diagnose (system->management), it says that internet is connected. But in the end it doesn't manage to send the report to ubuntu.

[remark: my system is german, so some program names might be slightly different - I'm translating them myself]

---

### Post by jonobr on 2008-12-22
Mmmmm.. weird Iowan, I know we post in or around the same time and you probably see my repeated comments on MTU,

see the one in this post?

---

### Post by Iowan on 2008-12-22
> **jonobr said:**
> see the one in this post?
Nope, but since you mention MTU, I notice MTU is 1320 when interface has an address, 1500 without one.

@jmmmp 
Your English is better than my German ever was...
> **jmmmp said:**
> And just in case, I did the ifconfig up / down afterwards. the result of route -n has only the first line of the above notated output.Wait... you mean the routing information *disappeared* after **ifconfig eth0 down/up**? Did IP address disappear too? (Wonder if it needs **dhclient** run?)

---

### Post by jmmmp on 2008-12-22
> **Iowan said:**
> 
Wait... you mean the routing information *disappeared* after **ifconfig eth0 down/up**? Did IP address disappear too? (Wonder if it needs **dhclient** run?)

Can you tell me a bit more detailed what to do? I know a bit of console operations, but am not familiar with unix enough.

---

### Post by Iowan on 2008-12-22
I'm probably just confusing both of us by thinking through keyboard (if you call it thinking...), but try running **dhclient** from a terminal (or **sudo dhclient** if permission is denied).  Check the results of previous commands (route, ifconfig, etc.) to see if information changes.  I'm afraid I may be taking you off-track of the original problem...

---

### Post by albinootje on 2008-12-22
> **jmmmp said:**
> Can you tell me a bit more detailed what to do? I know a bit of console operations, but am not familiar with unix enough.

Looking at the last bits of your posted output of commands, there's 192.168.1.1 as gateway, and as DNS-server.
But can you ping a public ip-address on the net ?
For example :
```

ping -c 3 62.108.1.65

```
And can your actually ping the gateway ? Just in case.
```

ping -c 3 192.168.1.1

```

---

### Post by jmmmp on 2008-12-23
Hi Iowan and albinootje,

Ping works around the house (192.168.1.x), but sometimes not outside, sometimes yes (with no change to other programs). If I log in and try the ping, it can't access the net. After doing a shclient, it does access it as normal - but no other programs have access to it, including synaptic.

here are the results of the command series (big output):

eth0      Link encap:Ethernet  Hardware Adresse 00:1c:25:cb:11:02  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:25ff:fecb:1102/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metrik:1
          RX packets:41 errors:18 dropped:0 overruns:0 frame:18
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6340 (6.1 KB)  TX bytes:10335 (10.0 KB)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:78700 (76.8 KB)  TX bytes:78700 (76.8 KB)

[after sudo dhclient]

eth0      Link encap:Ethernet  Hardware Adresse 00:1c:25:cb:11:02  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:25ff:fecb:1102/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metrik:1
          RX packets:118 errors:36 dropped:0 overruns:0 frame:36
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:16008 (15.6 KB)  TX bytes:21391 (20.8 KB)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:78700 (76.8 KB)  TX bytes:78700 (76.8 KB)

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

[after sudo ifconfig eth0 down/up]


eth0      Link encap:Ethernet  Hardware Adresse 00:1c:25:cb:11:02  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21c:25ff:fecb:1102/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metrik:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:3058 (2.9 KB)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:78700 (76.8 KB)  TX bytes:78700 (76.8 KB)

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

---

### Post by albinootje on 2008-12-23
> **jmmmp said:**
> Ping works around the house (192.168.1.x), but sometimes not outside, sometimes yes (with no change to other programs). If I log in and try the ping, it can't access the net. After doing a shclient, it does access it as normal - 

Sounds like a network-manager problem to me.
You could uninstall Network-manager and try wicd.
> 
but no other programs have access to it, including synaptic.

Does your firewall enforce the use of a proxy ?

---

### Post by jmmmp on 2008-12-23
> **albinootje said:**
> Sounds like a network-manager problem to me.
You could uninstall Network-manager and try wicd.
Sorry, but I've seen the network settings window, and there's nothing there about network manager. also typing wicd in the console doesn't do anything.


> **albinootje said:**
> Does your firewall enforce the use of a proxy ?
I don't even know if ubuntu has a firewall, I thought only windows had that. I don't use proxies on any other computers/systems - just connect and it works.

I'll just repeat: I never had access to the internet with ubuntu in this computer (but with windows, yes). after I installed ubuntu, didn't change anything yet to the base system - because synaptic doesn't access the internet.

If you give some suggestions of things to do, it would be helful if you say clearly what is to do, I'm not a unix guru - mainly because of things like these that make me drop now and then the idea to work with linux: for me, windows always worked out of the box, linux (whatever it was) never did.

---

### Post by albinootje on 2008-12-23
> **jmmmp said:**
> 
I'll just repeat: I never had access to the internet with ubuntu in this computer (but with windows, yes). after I installed ubuntu, didn't change anything yet to the base system - because synaptic doesn't access the internet.

Sorry, i misread your previous posting :( where you wrote "ping around the local network", I thought you had internet-access every now and then, except for Synaptic package manager.

---

### Post by andguent on 2008-12-23
It almost sounds as if your router half locked up. I've seen times when the router would only permit a certain number of computers online at once, and this was usually a temporary thing. This isn't uncommon with home-quality routers.

It might be worth removing the power from the router and modem for a few minutes, powering them back up, and then trying your connection again.

---

### Post by jmmmp on 2008-12-23
ahh, I'm not sure about the router thing: as I said before, I access the internet with no problems with the same computer (as I'm doing this moment) with windows - same ip, of course. actually, I never had any problem with too many computers on this router.

---

### Post by andguent on 2008-12-23
It doesn't matter to me either way if you try it, I just thought I would bring it up as an option. Whatever works for you. :)

---

### Post by jmmmp on 2008-12-24
Ah. What I wanted to say in my reply is that playing with the router really doesn't make a difference.
And if it would have worked, would it be necessary to switch the router off each time I needed to chango to linux?
Also, my laptop also has XP+ubuntu, and it doesn't give any problems with either system.

---

### Post by andguent on 2008-12-24
I've seen it occur a couple times where a home router would let the first 3-5 computers on the Internet, and then any new connections are blocked and ignored. Resetting it fixed the problem for 3-4 months. I would agree that this probably isn't your situation, but I figured it was an easy thing to check. I often work by testing the easy fixes first.

I have thick skin. Do whatever you want with my idea, just don't call me late to supper (or however that saying goes). :)

---

### Post by andguent on 2008-12-24
Have you changed any network settings manually at all? Most home networks should be plug and go. Running dhclient really should get you working.

> **jmmmp said:**
> 
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

[after sudo ifconfig eth0 down/up]
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

Just as an FYI, the top output here of route -n looks healthy. That last line that starts with "0.0.0.0  192.168.1.1" is important, as it means your computer has figured out who is in charge of your Internet connection (the router). Without that line, your computer will never find the Internet. The dhclient command should find that setting for you.

Please confirm that the last line of **route -n** has the "192.168.1.1", and that when you **cat /etc/resolv.conf** it still has "nameserver 192.168.1.1" in there. We need those two settings to be in there before anything really has a chance of working.

Lets try these commands if you would and post the output here. I very much would like to see the 3 lines of statistics at the end.
```
ping -c 6 www.google.com
ping -c 6 64.233.169.147
ping -c 10 `route -n|tail -1|cut -c 17-32`
```

---

### Post by jmmmp on 2008-12-24
hi (again),

I didn't change anything on the network settings (either on any computer, or on the router). On all other computers/systems (including XP on the same computer giving problems) internet works without any problem at all - just plug & play.

What baffles me is that the output looks really normal - even ubuntu's network tester (system menu) says that network is working. The problem is that it doesn't reach the programs (synaptic and firefox were just examples).

here are the results from what you told me to do. as you can see, it even pings the outside correctly (although sometimes it doesn't). I did these tests just after booting up. After that, I did sudo dhclient, and did the tests again. The only difference was that by route -n the 2nd line wasn't there (169.254.0.0 ...). But the result is the same, no internet for other programs.

[route -n]

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

[cat /etc/resolv.conf]

nameserver 192.168.1.1


PING [www.l.google.com](www.l.google.com) (74.125.43.147) 56(84) bytes of data.
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=1 ttl=241 time=44.5 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=2 ttl=241 time=44.8 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=3 ttl=241 time=44.3 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=4 ttl=241 time=44.5 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=5 ttl=241 time=44.1 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=6 ttl=241 time=44.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 44.010/44.416/44.892/0.367 ms


PING 64.233.169.147 (64.233.169.147) 56(84) bytes of data.
64 bytes from 64.233.169.147: icmp_seq=1 ttl=241 time=119 ms
64 bytes from 64.233.169.147: icmp_seq=2 ttl=241 time=116 ms
64 bytes from 64.233.169.147: icmp_seq=3 ttl=241 time=116 ms
64 bytes from 64.233.169.147: icmp_seq=4 ttl=241 time=117 ms
64 bytes from 64.233.169.147: icmp_seq=5 ttl=241 time=118 ms
64 bytes from 64.233.169.147: icmp_seq=6 ttl=241 time=117 ms

--- 64.233.169.147 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 116.631/117.590/119.164/0.944 ms


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=30 time=2.10 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=30 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=30 time=1.73 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=30 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=30 time=1.68 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=30 time=1.65 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=30 time=1.68 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=30 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=30 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=30 time=1.70 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8999ms
rtt min/avg/max/mdev = 1.649/1.720/2.100/0.129 ms
[route -n]

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

[cat /etc/resolv.conf]

nameserver 192.168.1.1


PING [www.l.google.com](www.l.google.com) (74.125.43.147) 56(84) bytes of data.
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=1 ttl=241 time=44.5 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=2 ttl=241 time=44.8 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=3 ttl=241 time=44.3 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=4 ttl=241 time=44.5 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=5 ttl=241 time=44.1 ms
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=6 ttl=241 time=44.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 44.010/44.416/44.892/0.367 ms


PING 64.233.169.147 (64.233.169.147) 56(84) bytes of data.
64 bytes from 64.233.169.147: icmp_seq=1 ttl=241 time=119 ms
64 bytes from 64.233.169.147: icmp_seq=2 ttl=241 time=116 ms
64 bytes from 64.233.169.147: icmp_seq=3 ttl=241 time=116 ms
64 bytes from 64.233.169.147: icmp_seq=4 ttl=241 time=117 ms
64 bytes from 64.233.169.147: icmp_seq=5 ttl=241 time=118 ms
64 bytes from 64.233.169.147: icmp_seq=6 ttl=241 time=117 ms

--- 64.233.169.147 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 116.631/117.590/119.164/0.944 ms


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=30 time=2.10 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=30 time=1.64 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=30 time=1.73 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=30 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=30 time=1.68 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=30 time=1.65 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=30 time=1.68 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=30 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=30 time=1.66 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=30 time=1.70 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8999ms
rtt min/avg/max/mdev = 1.649/1.720/2.100/0.129 ms

---

### Post by albinootje on 2008-12-24
> **jmmmp said:**
> 
PING [www.l.google.com](www.l.google.com) (74.125.43.147) 56(84) bytes of data.
64 bytes from bw-in-f147.google.com (74.125.43.147): icmp_seq=1 ttl=241 time=44.5 ms

You can ping websites, but Firefox does what ?
Does it jump to "offline mode" or does it timeout ?

If it jumps to "offline mode" it's a good idea to remove network-manager, and start using /etc/network/interfaces

Can you also show the output of :
```

sudo apt-get update

```
whenever you can ping a website successfully.

---

### Post by jmmmp on 2008-12-24
Hi,

Firefox just stands waiting (for godot, I guess).

Here's the output of cat /etc/network/interfaces 
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0


and sudo apt-get update (I interrupted it after 1h)
pinging seems to be one of the few ways of getting to the outside.


Hole:1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-de                                      
Hole:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-de                                  
Hole:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release.gpg [189B]                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-de                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-de                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-de                            
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                                                      
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Translation-de                                        
  Verbindung fehlgeschlagen [IP: 141.76.2.131 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                                             
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Translation-de                                  
  Verbindung fehlgeschlagen [IP: 141.76.2.131 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                                              
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Translation-de                                    
  Verbindung fehlgeschlagen [IP: 141.76.2.131 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                                                   
Fehl [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                                            
  Verbindung fehlgeschlagen
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Translation-de                                  
  Verbindung fehlgeschlagen [IP: 141.76.2.131 80]
Hole:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release.gpg [189B]                                                
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Translation-de                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                                         
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Translation-de                                            
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Translation-de                                              
Hole:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [892B]                                          
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Translation-de                                            
Fehl [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                                             
  Verbindung fehlgeschlagen
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                                    
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                                           
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release                               
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Packages                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages  
Hole:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [426B]                               
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Packages                                                          
Fehl [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                           
  Verbindung fehlgeschlagen
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Sources                                    
Fehl [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages                     
  Verbindung fehlgeschlagen
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Sources                              
Fehl [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                            
  Verbindung fehlgeschlagen
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Packages                               
Fehl [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                       
  Verbindung fehlgeschlagen
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Sources                                
Fehl [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                        
  Verbindung fehlgeschlagen
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Packages                             
Fehl [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                     
  Verbindung fehlgeschlagen
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Sources                              
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Sources
Hole:7 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Sources [892B]
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Packages                                                    
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Sources
Fehl [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Packages  
  Verbindung fehlgeschlagen [IP: 141.76.2.131 80]
99% [Warte auf Kopfzeilen (header)]                    
jmmmp@jmmmp-desktop:~$

---

### Post by albinootje on 2008-12-24
> **jmmmp said:**
> Hi,

Firefox just stands waiting (for godot, I guess).

Here's the output of cat /etc/network/interfaces 
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0


and sudo apt-get update (I interrupted it after 1h)
pinging seems to be one of the few ways of getting to the outside.


Thanks.
It looks like it's too hard to get your Ubuntu-box online like this (in this long thread). :(

If you're still interested in using Ubuntu I suggest to use it inside VirtualBox on your Windows-machines, then you should have internet access inside Ubuntu for sure.
Make sure after installing Ubuntu in VirtualBox that you install the Guest Additions to have "seamless" mouse movements and full screen access.

---

### Post by jmmmp on 2008-12-25
thanks, but that's not really a substitute for ubuntu. for that I would had kept to xp.

do you know any other place where it might be possible to look for help?

I just installed the latest version - 8.10, and the result is exactly the same. on the screen everything looks ok, but in reality no internet for anybody.

Joao

---

### Post by Xnyper on 2008-12-26
I believe I'm having the same problem.  I had Gutsy on my laptop, and I remember that as soon as I typed in my WPA key I was online and had every bit of connectivity I expected.  I just upgraded to Intrepid, and now I can't get out to the net.

I know its not a router/ISP issue because I'm online on my hardy box (desktop) right now through the very same router.

I can ping my router, but I can't ping google.com.

DHCP seems to be working ok, 'cause my ip address looks good.

I'm going to investigate the issue, if I come up with anything I'll report back here.

---

### Post by albinootje on 2008-12-26
> **Xnyper said:**
> I believe I'm having the same problem.  I had Gutsy on my laptop, and I remember that as soon as I typed in my WPA key I was online and had every bit of connectivity I expected.  I just upgraded to Intrepid, and now I can't get out to the net.

I know its not a router/ISP issue because I'm online on my hardy box (desktop) right now through the very same router.

I can ping my router, but I can't ping google.com.

DHCP seems to be working ok, 'cause my ip address looks good.

I'm going to investigate the issue, if I come up with anything I'll report back here.

Please post the output of the following :
```

lshw -c network
ifconfig -a
route -n
cat /etc/resolv.conf

```

---

### Post by Xnyper on 2008-12-26
lshw -c network```
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:a3:7c:72
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:d7:3b:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.101 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:78:79:5d:80:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
ifconfig -a ```
eth0      Link encap:Ethernet  HWaddr 00:13:a9:a3:7c:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15500 (15.5 KB)  TX bytes:15500 (15.5 KB)

pan0      Link encap:Ethernet  HWaddr b6:78:79:5d:80:e9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d7:3b:88  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fed7:3b88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1248315 (1.2 MB)  TX bytes:185004 (185.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-D7-3B-88-62-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Route -n ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

cat /etc/resolv.conf ```
# Generated by NetworkManager
nameserver **205.171.3.65**

```

I was able to get it working by statically assigning my IP address and then changing the ip address in /etc/resolv.conf to 205.171.3.65, which I got off of my DSL modem's "status" page.  It had been 192.168.1.15.  I'm not sure where it came from, but it doesn't exist on my network (or at least it doesn't reply to pings).

---

### Post by jmmmp on 2008-12-30
Hi,

may I ask you to explain a bit more detailed what you did, as in a step-by-step thing? This internet thing is really putting me off, and noone seems to be able to help. As I need to have all my computers configured the same way, I'm almost considering leaving ubuntu.

---

### Post by albinootje on 2008-12-30
> **jmmmp said:**
> Hi,

may I ask you to explain a bit more detailed what you did, as in a step-by-step thing? This internet thing is really putting me off, and noone seems to be able to help. As I need to have all my computers configured the same way, I'm almost considering leaving ubuntu.

Do you have an open thread about that still ?
Can you give the url of that ?

---

### Post by jmmmp on 2008-12-30
Hi Albinootje,

this is still the open thread, as the problem wasn't solved yet.

Another friend of mine suggested that the problem must be in the router configuration, something isn't properly setup - although with this configuration (in which I changed nothing from the standard settings) I have no problems with ubuntu on my laptop, and on xp on the desktop. Only ubuntu on my desktop doesn't work. If necessary (or it makes sense), I can put some screenshots of the router settings.

---

### Post by Xnyper on 2008-12-30
Sorry for the delay, here's what I did--hope it works for you.


First of all, we need to find the address of your router.  If you type that IP into a browser it should take you to the router's user interface.

Based on what I read in your prior posts, I think that your default gateway is: [192.168.1.1]("192.168.1.1") Type that into a browser's address bar (or click the link).

If that doesn't do it (that is, if your browser doesn't take you to your router setup page) boot up your your XP box and type this into a command prompt:```
ipconfig
```It should tell us the correct default gateway.  

Once you're logged into your router, try to find a "status," "information," or "statistics" tab.  Once there, look for DNS addresses.  Here's what mine looked like:  	
```
  	  	  	DNS 1: 	*192.168.0.1* 	  	 
  	  	  	DNS 2: 	**205.171.3.65 **	  	 
  	  	  	DNS 3: 		  	 
  	  	  	MTU: 	1500
```

You're looking for a DNS ip that doesn't start with 192.168.*.* or 10.*.*.*

Notice in my configuration, there is a 192.168.0.1.  That is my modem's IP (it's a separate box).  If I didn't find DNS information on my router, I would have gone looking in my modem.

Next, I went to system --> preferences --> network configuration.  selected the network connection (in your case probably auto eth0) and clicked edit.

From there I selected the IPV4 settings tab and changed Auto (DHCP) to manual.  I filled out the table there, 
IP: 192.168.1.* (* = any unusued address)
Mask: 255.255.255.0 
gateway: <your gateway from above here>
DNS servers: <your DNS server from above>

click OK, and then Close.

Now, the way I understand it, /etc/resolv.conf should automatically get your DNS information because we entered it into network configurations.  It should do this each time you plug the ethernet cable in.  For me, it doesn't--or at least not correctly.  So, I open up a terminal and type ```
gksu gedit /etc/resolv.conf
``` and add the following line to it:```
nameserver <DNS IP from above>
```

After saving the file, I start getting through to the internet.

I don't fully understand everything I did, just 'been messing around until something worked.  I'll do my best to help you troubleshoot further, but I can't make any promises.

By the way, I think your friend is right, and this is a router setting issue--I never have trouble at anybody else's house.

---

### Post by oygle on 2008-12-31
jmmmp - can you modify /etc/network/interfaces (take backup first), so that it looks like this 

> auto lo
iface lo inet loopback
#iface eth0 inet dhcp
auto eth0

This is based on many suggestions in a thread about a bug in NM, see this post - [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262/comments/17](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262/comments/17) in particular

Then restart networking of course.

I have been trying to solve a NM problem myself but no-one has a solution yet (ppp0 and eth0 will not work concurrently).

Oygle

---

### Post by jmmmp on 2009-01-02
Hi Xnyper,

a couple days late, a reply. Things aren't working yet, but here are some details:

- I couldn't find a dns chart on my router or modem - only ip/mac adress. I always had dns automatic, and afaik they're always 192.168.1.1 in all computers in the house. Also when I do ifconfig on the problematic computer, the gateway is usually the same. do you know if there's any other place to get the dns info than the router? (probably not)

- I had also tried at some point to do a manual connection, by copying all the data. it hadn't worked already before, anyway. one funny thing: in the ipv4 section when I write the netmask of 255.255.255.0 (the right one) if accepts it. but when I come back to the window later, it changes it to 24. do you know where this information is stored, so that I can see if there's a problem with the dialog?
(I was speaking of the networks connection settings, in case that wasn't clear)

- the information in /etc/resolv.conf was already correct, anyway. I mean, it matched the data from ifconfig - 192.168.1.1.

---

### Post by jmmmp on 2009-01-02
Hi oygle,

I tried your suggestion, but nothing changed. Later I'll see what happens when I make up my own static condiguration in "interfaces". And also look at that whole thread.

---

### Post by aragon_1.0 on 2009-01-02
I may be little late to join this discussion but I would like to know the following things

1. what kind of Internet connection are you using.

2. If you are using a DSL line have you tried configuring PPPoE using the utility 'pppoeconf'

3. Quite simply tell us how does your windows connect to the internet or if you dont understand just tell us the name of the application you use to get connected to internet and do you use any username/password combinations to get it working ?

4. If all else fails use an 'ethereal' on windows at the time of getting connected to internet and post the output of ethereal on this forum so we can know what is your windows doing to get connected to internet

5. Finally your ethernet driver may not be working in linux, have you tried ping etc to another computer in the vicinity from your ubuntu system

---

### Post by jmmmp on 2009-01-02
Hi Aragon,

I'll be repeating myself now, I think this information is already somewhere in the x number of pages of this thread:

> **aragon_1.0 said:**
> I may be little late to join this discussion but I would like to know the following things

1. what kind of Internet connection are you using.

dsl connection, 1&1 germany.

> **aragon_1.0 said:**
> 2. If you are using a DSL line have you tried configuring PPPoE using the utility 'pppoeconf'

Don't even know what that is, so the answer should be no.

> **aragon_1.0 said:**
> 3. Quite simply tell us how does your windows connect to the internet or if you dont understand just tell us the name of the application you use to get connected to internet and do you use any username/password combinations to get it working ?

windows + ubuntu on my laptop (+ all other computers that got connected here, more windows and macOs) just connect to the lan or wireless, and it works, just like that.
the fritz modem gets the dsl signal, and then after that there's a router for the whole house. all other computers/systems work without problems with this though dhcp.

> **aragon_1.0 said:**
> 4. If all else fails use an 'ethereal' on windows at the time of getting connected to internet and post the output of ethereal on this forum so we can know what is your windows doing to get connected to internet

I can even use that on ubuntu on my laptop. or on xp on the same desktop that is giving problems.
I just installed wireshark on ubuntu (laptop), but it doesn't list any interface to capture. Do I have to run it as root? I get a notice saying that it's dangerous to do that.

> **aragon_1.0 said:**
> 5. Finally your ethernet driver may not be working in linux, have you tried ping etc to another computer in the vicinity from your ubuntu system

As I probably already said, ping works also for the outside world. I can even access the windows shares on my laptop through samba. I just can't get internet with any program on my desktop+ubuntu.

---

### Post by aragon_1.0 on 2009-01-03
As I see it almost everything is alright and most probably the thing going wrong here is DNS resolution not taking place, the fact that you are able to connect to other computers in the LAN itself means your computer's networking is working alright, now the only problem seems to be two things 

1. Packets not getting routed to the destinations. Now this could be bacause 

   a) DNS's not getting resolved, so rather than trying to browse [www.yahoo.com](www.yahoo.com) why not you try to browse using IP address of [www.yahoo.com](www.yahoo.com) --I believe you must be knowing how to find this -- which would mean you are bypassing the DNA resolution and if you are able to get to the site then there is the problem. so its just a matter of adding right IP addresses to the /etc/resolv.conf file

  b) Your default router must be IP address of the router you are using in the LAN, now if this too is alright then move to the next point

2. Packets getting dropped at the router or packets could be getting dropped just at your computer, now this could be from source side or destination side (i.e the web-site you are trying to browse)

    This could be due to some firewall at the router or at your computer just check if there's any.


As a matter of testing by trial and error I suggest you do the following simple exercise if you have one router and two computers -- PCs --

Put each computer on a separate network i.e give IP 192.168.1.2 to first computer and 192.168.2.2 to other one, now setup the router's ethernet interface to first computer with IP 192.168.1.1 and the ethernet interface to second computer as 192.168.2.1 

now  in first computer add as default route 192.168.1.1 and in the second computer add default route as 192.168.2.1

the way you do this in linux is "route add default gw 192.168.1.1" 

Now ping from one computer to other 

e.g from first computer ping to second computer as 'ping 192.168.2.2' and vice-versa

Now if you can get this working then your computer is all set. just let me know

---

### Post by jmmmp on 2009-01-04
Hi everyone,

someone else told me what was wrong, the mtu setting. For now it works when I put in
```
sudo ifconfig eth0 mtu 1500
```
so now I only need to look around on how to set this automatically (or in the router).

Thanks for your help. I'll write something when I have it 100% finished.

Joao

---

### Post by Xnyper on 2009-01-12
Glad you got it taken care of.

Just thought I'd mention, since you brought it up, that a mask of 255.255.255.0 represents 24 bits on (and the remaining 8 off), so that's why it changes it for you--I guess to let you know that there is a shorter way to type it in.

---


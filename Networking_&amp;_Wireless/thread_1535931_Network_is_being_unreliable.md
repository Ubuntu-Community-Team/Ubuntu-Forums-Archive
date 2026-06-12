---
title: "Network is being unreliable"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Pandyrenim on 2010-07-21
I am running Ubuntu 9.04 And i have been running it for sometime. I also have another hard drive in my computer that has Windows Xp that i never use because it is suffering a similar problem. I upgraded my Ubuntu when 10 came out but my Internet wouldn't work. I looked for the problem and i found that i had no drivers, none at all. Well i couldn't download any because of no Internet connection. Well I reverted to 9.04 and my internet works now, But there is one problem, When i start up my computer i have about a 50 50 chance of it picking up my Internet connection. I'm not sure what kind of net card I'm using or even how to check.

Does anyone have any ideas?

Oh and my windows partition just doesn't connect to the Internet at all

Ps. I'm connected via hardwire

---

### Post by Iowan on 2010-07-21
**sudo lshw -C network** will reveal information about your network card (including driver, alias, ...)

---

### Post by Pandyrenim on 2010-07-22
This is what the system gives me when i put that in
  *-network               
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 00:13:20:7e:e6:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.0-5 ip=192.168.1.7 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:e8:ea:48:d2:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by dineshs on 2010-07-22
Can you post the output of ```
route -n
```and```
ping 4.2.2.1 -c3
```_when you have problem_

---

### Post by Pandyrenim on 2010-07-22
These are the outputs that you had requested

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

ping 4.2.2.1 -c3
connect: Network is unreachable

---

### Post by Iowan on 2010-07-22
Interesting - interface (eth0) has an IP address, but no route - anywhere. Is that a DHCP address - or did you set up a static address?

---

### Post by Pandyrenim on 2010-07-22
i'm not sure at the moment, i have to take off for work right now, bu i will check into it and give you guys a bunch of info when i get home later tonight

I checked my network stats and DHCP is set to automatic

---

### Post by Pandyrenim on 2010-07-24
i wouldn't know how to set up a static connection so i doubt that i have that going either

---

### Post by Pandyrenim on 2010-07-29
Still haven't solved this, if there are any ideas, would buying a new Ethernet card work?

---

### Post by Pandyrenim on 2010-08-03
Please if anyone can think of anything it would help alot, this problem is becoming increasingly annoying because my system likes to fart around when booting and takes about 3 minutes, very frustrating early in the morning

---

### Post by dineshs on 2010-08-03
what do you get when you run
```
sudo dhclient
```when your modem/router is connected and is ON

---

### Post by Pandyrenim on 2010-08-05
> **dineshs said:**
> what do you get when you run
```
sudo dhclient
```when your modem/router is connected and is ON

Listening on LPF/pan0/7a:54:b6:fc:63:13
Sending on   LPF/pan0/7a:54:b6:fc:63:13
Listening on LPF/eth0/00:13:20:7e:e6:38
Sending on   LPF/eth0/00:13:20:7e:e6:38
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 39838 seconds.

this is what i get

---

### Post by dineshs on 2010-08-05
You are connected to the router/modem.Pl post the output of
```
ifconfig -a
```
```
ping 192.168.1.1 -c3
```
```
ping 4.2.2.1 -c3
```and```
ping www.google.com -c3
```

---

### Post by Pandyrenim on 2010-08-05
> **dineshs said:**
> You are connected to the router/modem.Pl post the output of
```
ifconfig -a
```
```
ping 192.168.1.1 -c3
```
```
ping 4.2.2.1 -c3
```and```
ping www.google.com -c3
```

out puts in order
1)
eth0      Link encap:Ethernet  HWaddr 00:13:20:7e:e6:38  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe7e:e638/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1470785 (1.4 MB)  TX bytes:319525 (319.5 KB)
          Memory:88100000-88120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 8e:6c:40:ad:9e:6a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
2)
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.843 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.21 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.522 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.522/0.861/1.218/0.284 ms

3)
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=54 time=20.7 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=54 time=20.0 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=54 time=19.8 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 19.826/20.183/20.724/0.405 ms

4)
PING [www.l.google.com](www.l.google.com) (209.85.225.104) 56(84) bytes of data.
64 bytes from iy-in-f104.1e100.net (209.85.225.104): icmp_seq=1 ttl=52 time=30.0 ms
64 bytes from iy-in-f104.1e100.net (209.85.225.104): icmp_seq=2 ttl=52 time=29.3 ms
64 bytes from iy-in-f104.1e100.net (209.85.225.104): icmp_seq=3 ttl=52 time=29.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 29.016/29.484/30.096/0.493 ms

there they are, i also wanted to thank you so much for helping me, i forgot to in my last post. I hope you can come up with something

---

### Post by dineshs on 2010-08-05
The results look normal.You have IP,you have reply from google.Now what exactly is your problem?Pages not loading ?

---

### Post by Pandyrenim on 2010-08-06
> **dineshs said:**
> The results look normal.You have IP,you have reply from google.Now what exactly is your problem?Pages not loading ?

No, when i boot up about 3/5 times it shows up as there being no connection, a reboot or two and it recognizes it

---

### Post by dineshs on 2010-08-06
Pl post the results of the commands in #13 and
```
sudo lshw -C network
```[COLOR="Purple"]When the connection is not working[/COLOR]

---


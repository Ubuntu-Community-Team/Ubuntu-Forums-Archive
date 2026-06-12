---
title: "Noonb Wired connection no connection"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by TopTrainer on 2010-04-12
[FONT=Arial]Hi
I am a Linux Ubuntu NooB wanting to transfer from Windows. i currently have latestest distro installed on a drive on its own (not duel boot). on a separate machine on my network. This machine previously ran Win Xp Home.

My connection is wired and states im connected Auto eth1 active. but sadly there is not connection to the internet .There must be something I am not doing here.Can someone please point me in the right direction as this is a basic requirement and I really want to make this change. Have tied to ping but zero

This mail comes from my other windows comp on the same network as the above described. Some help showing me how to access this machine from Unbutu machine would be great too.

Thanks

Pete[/FONT]

---

### Post by Iowan on 2010-04-12
From a terminal (Applications>Accessories>Terminal) enter:```
ifconfig -a
``` See if interface(s) have IP address. I'm curious that the machine set up eth1 - eth0 seems more normal (my laptop uses eth1 for wireless card) unless the machine has more than one wired card.

---

### Post by TopTrainer on 2010-04-13
Hi
Thanks for your reply eth1 has an address. also says loop back running  ? but no connection and no ping either

Peter

---

### Post by Iowan on 2010-04-13
What IP address is shown for eth1 (in particular - hope it's not 169.254.X.X - that's **avahi** trying to help). You mentioned no ping - is that by hostname or IP address (or both)? Can you ping the machine from the Windows machine you're using?  
(I'll eventually get around to having you **ifconfig -a > ifconfig.txt**, copying that file to removable media, and using your Windows machine to post it here).

---

### Post by TopTrainer on 2010-04-14
> **Iowan said:**
> What IP address is shown for eth1 (in particular - hope it's not  169.254.X.X - that's **avahi** trying to help). You mentioned no ping  - is that by hostname or IP address (or both)? Can you ping the machine  from the Windows machine you're using?  
(I'll eventually get around to having you **ifconfig -a >  ifconfig.txt**, copying that file to removable media, and using your  Windows machine to post it here).


[SIZE=2]Hi[/SIZE]
In answer to your questions:

connection informatin reads
Auto eth1 (default)
interface Ethernet 1
Hardware address 00:0C:6E:6A:2B:38
Driver via_rhine
Speed  100mb/s
Security none
IP Address 192.168.1.12
Broadcast Address  192.168.1.255
Subnet  255.255.255.0
Default route  192.168.1.1
Primary DNS 212.23.8.1
Secondary DNS 212.23.8.6

This is a wired connection I just pinged the IP =
**Ping test for 192.168.1.12**

 PING 192.168.1.12 (192.168.1.12) 56(84) bytes of data.
64 bytes from 192.168.1.12: icmp_seq=1 ttl=64 time=20.1 ms
64 bytes from 192.168.1.12: icmp_seq=2 ttl=64 time=0.429 ms
64 bytes from 192.168.1.12: icmp_seq=3 ttl=64 time=0.398 ms
64 bytes from 192.168.1.12: icmp_seq=4 ttl=64 time=1.74 ms
64 bytes from 192.168.1.12: icmp_seq=5 ttl=64 time=0.585 ms
64 bytes from 192.168.1.12: icmp_seq=6 ttl=64 time=0.559 ms
64 bytes from 192.168.1.12: icmp_seq=7 ttl=64 time=0.903 ms
64 bytes from 192.168.1.12: icmp_seq=8 ttl=64 time=0.373 ms
64 bytes from 192.168.1.12: icmp_seq=9 ttl=64 time=0.344 ms
64 bytes from 192.168.1.12: icmp_seq=10 ttl=64 time=0.441 ms

--- 192.168.1.12 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9008ms
rtt min/avg/max/mdev = 0.344/2.591/20.134/5.861 m

As a matter of interest I have re-installed ubuntu to see if things were changed no change. I also tried a live cd of Mandriva in this machine which also would showed a connection but would not conect to the internet.????


Peter

---

### Post by Iowan on 2010-04-14
I presume 192.168.1.12 is the Ubuntu box. If it can ping 192.168.1.1 (router?) we'll need to check contents of */etc/resolv.conf* - though it looks like the route is there (that doesn't look like output from **ifconfig**, though.

---

### Post by TopTrainer on 2010-04-15
Hi

Thanks for your help on this but im quite sure what you mean.I have done the ifconfig thing but im not able to save it ubuntu is not mounting my floppy drive  :confused:
Im having quite a bad feeling about this to be honest. If I put my windows drive in it connects fine so im not sure why it would not do it with linux

P

---


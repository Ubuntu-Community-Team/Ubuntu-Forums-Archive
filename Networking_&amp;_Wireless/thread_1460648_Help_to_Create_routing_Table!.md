---
title: "Help to Create routing Table!"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by MAO on 2010-04-23
Hi all!

Given:
1) From ISP INTERNET throe PPPoE:
Static WAN IP   217.29.11.11
Subnet Mask   255.255.255.255 
Gateway   217.29.22.22 
Primary DNS Server   217.29.16.249 
Secondary DNS Server   217.29.16.250 
Connection Mode   PPPoE
2) Take external IP's from 217.29.33.33 to 217.29.33.40  netmask 255.255.255.248

Need:

Server with two LAN Cards **eth0** (PPPoE from ISP 217.29.11.11) and **eth1** (external IPs from 217.29.33.33 to 217.29.33.40)


ISP ------ eth0 -----> eth1 ------ switch --------> servers

PLZ Help!!!!

---

### Post by Iowan on 2010-04-23
Is this on a CLI-based server (uses */etc/network/interfaces*) or a Network Manger controlled machine?

---

### Post by MAO on 2010-04-26
> **Iowan said:**
> Is this on a CLI-based server (uses */etc/network/interfaces*) or a Network Manger controlled machine?

CLI -based Server 9.10 (uses */etc/network/interfaces*)!

ISP Gives Gateway 217.29.33.34
IPs from 217.29.33.33 to 217.29.33.40
Netmask 255.255.255.248

---

### Post by MAO on 2010-04-27
Anyone !!!!

---

### Post by redmk2 on 2010-04-28
> **MAO said:**
> Hi all!

Given:
1) From ISP INTERNET throe PPPoE:
Static WAN IP   217.29.11.11
Subnet Mask   255.255.255.255 
Gateway   217.29.22.22 
Primary DNS Server   217.29.16.249 
Secondary DNS Server   217.29.16.250 
Connection Mode   PPPoE
2) Take external IP's from 217.29.33.33 to 217.29.33.40  netmask 255.255.255.248

Need:

Server with two LAN Cards **eth0** (PPPoE from ISP 217.29.11.11) and **eth1** (external IPs from 217.29.33.33 to 217.29.33.40)

ISP ------ eth0 -----> eth1 ------ switch --------> servers

PLZ Help!!!!

A few thoughts and questions:

Are you sure about that subnet mask?  

This would give you a network like this ```
217.29.33.32 /29 (255.255.255.248) with 6 hosts (33 to 38)
```  The range you have is either: to big or the mask is wrong.  

My bet is that the subnet mask is wrong.  Maybe it should be ```
217.29.33.32 /28 (255.255.255.240) with 14 hosts (33 to 46)
```

It looks like you are creating a router/gateway.  You need more than just routing.  You need to forward the packets from one interface to the other in the kernel (syscntl) and setup IPTABLES.

When it is all said and done, a cheap router is the fastest, cheapest (considering labor) way to go.

[**_Here _**]("http://www.cyberciti.biz/tips/linux-as-router-for-dsl-t1-line-etc.html")is a basic DSL router setup.  You DO NOT need the NAT part.  You do need to set up a fire wall with IPTABLES.

[**_This _**]("http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/")is just for IP forwarding.

---

### Post by MAO on 2010-04-30
Can Any one show me how t odo from 0 to the END?

I need:

ISP --- pppoe ----> eth0 ------------> eth1 ------> switch ----> Servers

---

### Post by MAO on 2010-05-03
what next?

---

### Post by MAO on 2010-05-06
Anyone PLZ Ubuntu GURU Where Are You !
here the picture [http://ubuntuforums.org/showthread.php?t=1474463](http://ubuntuforums.org/showthread.php?t=1474463)

---


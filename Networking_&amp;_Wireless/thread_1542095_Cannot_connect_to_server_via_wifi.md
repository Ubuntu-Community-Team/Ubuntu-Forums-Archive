---
title: "Cannot connect to server via wifi"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by nirvblakr on 2010-07-30
Hi! I have a Synology home server at home. I have a laptop with Linux Mint 8 (Helena) installed. I can access my server's shared files using LAN through Places>Network>Windows Network>Workgroup>Server>Shared files. I can also access the files through a web browser. Samba is installed. The problem is when I use the wireless lan of my laptop, I cannot access the server and the files anymore locally even through a web browser.

I tried Connect to Server through Windows Share but what I get is "Could not display "smb://server/".".

Any help would be appreciated. Thanks!

---

### Post by Iowan on 2010-07-30
Can you ping the machine via wireless connection?

---

### Post by nirvblakr on 2010-07-31
> **Iowan said:**
> Can you ping the machine via wireless connection?


How do you I go about it? 

The local ip address of the server is 192.168.11.6:5000.

---

### Post by Iowan on 2010-08-01
From a terminal (Applications>Accessories>Terminal):
**ping -I wlan0 192.168.11.6**
Assuming your wireless interface is wlan0 - my laptop has the wireless as eth1. You can check via **ifconfig -a**. The wireless interface *should* have an address in the 192.168.11.X subnet.

---

### Post by nirvblakr on 2010-08-02
> **Iowan said:**
> From a terminal (Applications>Accessories>Terminal):
**ping -I wlan0 192.168.11.6**
Assuming your wireless interface is wlan0 - my laptop has the wireless as eth1. You can check via **ifconfig -a**. The wireless interface *should* have an address in the 192.168.11.X subnet.

Thanks for the reply.

This is what I got:

PING 192.168.11.6 (192.168.11.6) from 192.168.11.5 wlan0: 56(84) bytes of data.
From 192.168.11.5 icmp_seq=1 Destination Host Unreachable
From 192.168.11.5 icmp_seq=2 Destination Host Unreachable
From 192.168.11.5 icmp_seq=3 Destination Host Unreachable
From 192.168.11.5 icmp_seq=4 Destination Host Unreachable
From 192.168.11.5 icmp_seq=5 Destination Host Unreachable
...

---

### Post by Iowan on 2010-08-02
That doesn't look especially good...
What are results of **route -n**?

---

### Post by nirvblakr on 2010-08-04
> **Iowan said:**
> That doesn't look especially good...
What are results of **route -n**?

I'm sorry sir but I do not know how to go about this.  I am just a newbie.  Should I just type route -n?

---

### Post by bkratz on 2010-08-04
> **nirvblakr said:**
> I'm sorry sir but I do not know how to go about this.  I am just a newbie.  Should I just type route -n?


Sorry for the intrusion, ( since he may not be back for hours ) but that is exactly what he wants, just go to the terminal (like before) enter it and copy/paste the results  back here.

---

### Post by Iowan on 2010-08-04
> **bkratz said:**
> Sorry for the intrusion, ( since he may not be back for hours ) ... Not an intrusion - thanks for the input. (For some reason, the company that occasionally tosses change my way seems to think I should show up and earn it...)

---

### Post by nirvblakr on 2010-08-05
> **Iowan said:**
> That doesn't look especially good...
What are results of **route -n**?

OK.  Here's what I got:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0

---

### Post by Iowan on 2010-08-05
Can you **ping** the router (192.168.11.1)?

---

### Post by nirvblakr on 2010-08-09
> **Iowan said:**
> Can you **ping** the router (192.168.11.1)?

This is what I got:

PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.
64 bytes from 192.168.11.1: icmp_seq=1 ttl=64 time=1.91 ms
64 bytes from 192.168.11.1: icmp_seq=2 ttl=64 time=3.27 ms
64 bytes from 192.168.11.1: icmp_seq=3 ttl=64 time=1.35 ms
64 bytes from 192.168.11.1: icmp_seq=4 ttl=64 time=1.53 ms
.....

---

### Post by Iowan on 2010-08-09
I suppose I should have asked earlier if the laptop is connected via wire AND wireless. I'm assuming the previous response was via wireless, but you can double-check with :
**ping -I wlan0 192.168.11.1**

---

### Post by nirvblakr on 2010-08-09
> **Iowan said:**
> I suppose I should have asked earlier if the laptop is connected via wire AND wireless. I'm assuming the previous response was via wireless, but you can double-check with :
**ping -I wlan0 192.168.11.1**

I always try to access the server using wifi as per your instructions.  If I connect my laptop via LAN cable, I can access the server files with no problems. [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

---

### Post by nirvblakr on 2010-08-10
> **Iowan said:**
> I suppose I should have asked earlier if the laptop is connected via wire AND wireless. I'm assuming the previous response was via wireless, but you can double-check with :
**ping -I wlan0 192.168.11.1**

This is what I got:

PING 192.168.11.1 (192.168.11.1) from 192.168.11.10 wlan0: 56(84) bytes of data.
64 bytes from 192.168.11.1: icmp_seq=1 ttl=64 time=1.57 ms
64 bytes from 192.168.11.1: icmp_seq=2 ttl=64 time=1.34 ms
64 bytes from 192.168.11.1: icmp_seq=3 ttl=64 time=1.32 ms
64 bytes from 192.168.11.1: icmp_seq=4 ttl=64 time=1.34 ms
64 bytes from 192.168.11.1: icmp_seq=5 ttl=64 time=1.31 ms
64 bytes from 192.168.11.1: icmp_seq=6 ttl=64 time=1.32 ms
64 bytes from 192.168.11.1: icmp_seq=7 ttl=64 time=1.33 ms
64 bytes from 192.168.11.1: icmp_seq=8 ttl=64 time=1.33 ms
64 bytes from 192.168.11.1: icmp_seq=9 ttl=64 time=1.33 ms
64 bytes from 192.168.11.1: icmp_seq=10 ttl=64 time=1.34 ms
64 bytes from 192.168.11.1: icmp_seq=11 ttl=64 time=1.33 ms
64 bytes from 192.168.11.1: icmp_seq=12 ttl=64 time=1.34 ms
64 bytes from 192.168.11.1: icmp_seq=13 ttl=64 time=1.33 ms
64 bytes from 192.168.11.1: icmp_seq=14 ttl=64 time=1.32 ms
64 bytes from 192.168.11.1: icmp_seq=15 ttl=64 time=951 ms
64 bytes from 192.168.11.1: icmp_seq=16 ttl=64 time=1.41 ms
64 bytes from 192.168.11.1: icmp_seq=17 ttl=64 time=1.32 ms
64 bytes from 192.168.11.1: icmp_seq=18 ttl=64 time=1.34 ms
....

By the way,  I can also access my router's settings through wifi.

---


---
title: "Cannot connect a 2nd ubuntu pc to network."
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by ccaltabiano on 2008-12-14
Hi.
i am running Ubuntu 7.10 on my desktop, and i recently installed it on my laptop. now, my laptop not able to connect to network with Ethernet while my pc is on.

i have set IP to static on both desktop and laptop, would the localhost IP have anything to do with it as it is the same for both PC's?

has anyone had this issue?
any help would be much appreciated.

regards,
Christian

---

### Post by bluefrog on 2008-12-14
a network cannot have the same IP on different machines. (can't put two feet in one shoe, right?)
change the IP of one machine and your problem will be solved.

---

### Post by ccaltabiano on 2008-12-16
i changed the local host IP. still have same issue.
can i ask what the localhost IP is???

---

### Post by gpsmikey on 2008-12-16
The localhost 127.0.0.1 is the "loopback address" (sort of like "home").  It should be that address on all machines.  The IP address of the machines needs to be different though.  What is the address of your router and what addresses do you have for the two machines ??

mikey

---

### Post by Iowan on 2008-12-16
> **ccaltabiano said:**
> ... my laptop not able to connect to network with Ethernet while my pc is on.

i have set IP to static on both desktop and laptop, would the localhost IP have anything to do with it as it is the same for both PC's?

Will it connect when PC is off?
As mentioned, localhost should have address 127.0.0.1 
FYI, if you look in /etc/hosts file, there is *probably* another line (127.0.1.1 <yourhostname>) that should be left.  Running **ifconfig** (from a terminal) should show you the IP address assigned to your interface (eth0?).  The two machines should have a unique address, but still in the same subnet (meaning, probably only the last digit should be different - eg. 192.168.1.X, where X is the "unique" value between 2 and 254).

---


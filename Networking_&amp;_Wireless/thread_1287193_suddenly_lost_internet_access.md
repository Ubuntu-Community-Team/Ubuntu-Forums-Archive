---
title: "suddenly lost internet access"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by wired99 on 2009-10-09
I'm using Ubuntu Hardy 8.04 and suddenly lost my internet access while downloading a file.

I have 2 computers (one with Vista, the other Ubuntu) and a printer individually connected to a router which in turn is connected to a DSL modem.

From Ubuntu I can ping my Vista computer and the printer. I also have access (with Ubuntu) to my shared folder in Vista.

I cannot ping the router.
I cannot access the internet with Ubuntu 

What can I do?

---

### Post by wired99 on 2009-10-09
I tried running a Live CD (Linux Mint 7) and it cannot access the internet either (it did previously)
I have Jaunty in a secondary disc drive and it too cannot access the internet

---

### Post by Iowan on 2009-10-10
> **wired99 said:**
> I cannot ping the router.
I cannot access the internet with Ubuntu 

What can I do?Does interface have IP Address? (**ifconfig -a**)

---

### Post by wired99 on 2009-10-11
interestingly the command "ipconfig -a" is not found...

However, as mysteriously as I lost the internet access it suddenly returned a few days later, I did not configure nor edit any files. (nor were any updates - since I had not internet access)

I don't know why I lost it nor how it returned, but my internet is up and running now from Ubuntu  ???

---

### Post by Iowan on 2009-10-11
> **wired99 said:**
> interestingly the command "ipconfig -a" is not found...
AWWWWW... fumble, typo, or Window-ed. Shoulda been **ifconfig -a**
Glad it works - again... Give it a few days before marking the thread [SOLVED] (Thread Tools).

---

### Post by kpiascik on 2009-10-24
I'm having the same issue.
I just lost my outbound internet access in Ubuntu 8.10

The setup I have is a Ubuntu connected to router connected to cable modem.

The weird thing is that I can putty into my computer and I can connect to the apache web server running on Ubuntu, but I can't ping my router from Ubuntu nor can I connect to the internet.

Also I can ping my own network IP 192.168.0.101

here is what ifconfig -a results:
eth0      Link encap:Ethernet  HWaddr 00:16:17:38:b5:a6
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe38:b5a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26867228 (26.8 MB)  TX bytes:508832016 (508.8 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4292 (4.2 KB)  TX bytes:4292 (4.2 KB)

pan0      Link encap:Ethernet  HWaddr 3a:79:3d:12:7f:1f
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Iowan on 2009-10-24
Is that a DHCP or static address?

---


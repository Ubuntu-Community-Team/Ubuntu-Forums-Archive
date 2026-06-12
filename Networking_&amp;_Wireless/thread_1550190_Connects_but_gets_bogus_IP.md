---
title: "Connects but gets bogus IP"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by bazianm on 2010-08-10
Hi,

I just reformatted a Dell Inspiron 640m notebook with Ubuntu Desktop 10.04. I guess I should state up front that I am mostly a Windows guy and am working with Ubuntu to get into it.

Anyway, I can connect wired to my office network no problem.

I can see wireless networks around me (the wireless card is the Dell Wireless 1390) and it says it is connected to my office wireless. The problem is that the IP address as reported by network tools is totally bogus. My office network is 192.168.42.x whereas the IP address reported by Network Tools for this connection is 10.42.43.1 (I wonder if this is the functional equivalent of the bogus IP address Windows gives me when it can't get an IP address).

I know that the wireless network is working because my work laptop (Windows XP) connects to it just fine and the WAP is just a few feet behind me in the other office.

I tried installing the windows drivers from Dell to no avail. I tried the Broadcom STA drivers to no avail.

I am stumped. Any suggestions would be appreciated.

Thanks in advance!

---

### Post by Iowan on 2010-08-10
**avahi** also uses the ZeroConf network 169.254.X.X. It's probably the same, but from a terminal (Applications>Accessories>Terminal), check **ifconfig -a** as a double-check on the IP address.

---

### Post by pricetech on 2010-08-10
What IP does your windows box get ??

---

### Post by bazianm on 2010-08-10
Here's the results from the ubuntu box:
wlan0     Link encap:Ethernet  HWaddr 00:0e:a6:f9:ca:81  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef9:ca81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1478339 (1.4 MB)  TX bytes:11339 (11.3 KB)

As for the windows box, the wireless connection has 192.168.42.62

---

### Post by bazianm on 2010-08-11
Here's another interesting issue. I brought the notebook into a client which has a wireless network but I do not have the wep key for the network and cannot log in. The notebook, upon bootup, said that it was connected to my **home network** which, of course, is impossible because that is many miles away...

Any thoughts?

---


---
title: "Configuring internet in Ubuntu10.04"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by a2l007 on 2010-06-11
Hello  to everyone at ubuntu forums. I recently bought a dell inspiron 14 n4010 and i've installed windows and Ubuntu 10.04 in it.
 The problem is that i'm not able to access internet in my ubuntu. I'm using asianet broadband connection and i'm able to get internet in my desktop when i connect the cable to the system.
But when i did the same with ubuntu 10.04 in my laptop, i'm not able to get internet access.
I'm able to access internet in  windows though. But i hate using windows. can anyone suggest me a solution to configure my net connection ?



Thanks in advance..

---

### Post by ufis on 2010-06-11
If it is only your firefox browser that cannot connect do the following:

open firefox
in the address bar type: **about:config**
click the "**I'll be careful**" button.
in the filter box type: **network.dns.disableIPv6**
double click the "false" value on the network.dns.disableIPv6 line to set it to **true**

try connecting again

---

### Post by a2l007 on 2010-06-11
Thanks for the reply. I'm afraid, its not the problem with only firefox. There are no connections detected in the network connections menu. And ur suggested solution did nt work.  How do i configure a new connection?

---

### Post by a2l007 on 2010-06-11
Thanks for the reply. I'm afraid, its not the problem with only firefox. There are no connections detected in the network connections menu. And ur suggested solution did nt work.  How do i configure a new connection?

---

### Post by Iowan on 2010-06-11
In a terminal (Applications>Accessories>Terminal) check **ifconfig -a** to see if the interface has an IP address. If so, you might try pinging an internet site by name (google.com) or IP address (74.125.95.103).

---

### Post by The Low End Theory on 2010-06-11
try plugging your laptop into your router with an ethernet cable, then going to system>administration>hardware drivers your driver should appear there, you may have to enable it, but after that it should work fine

---

### Post by a2l007 on 2010-06-12
Thanks for replying. This is the output that i recieve when i ran ifconfig -a. Is it of any help in finding the solution.Pinging google gives the error unknown host

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16080 (16.0 KB)  TX bytes:16080 (16.0 KB)

pan0      Link encap:Ethernet  HWaddr da:36:2c:09:64:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Actually my laptop is connected to the router via ethernet cable.I checked the hardware drivers category but it showed "no proprietary.

---

### Post by varspare on 2010-06-12
> **a2l007 said:**
> 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16080 (16.0 KB)  TX bytes:16080 (16.0 KB)

pan0      Link encap:Ethernet  HWaddr da:36:2c:09:64:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Your ethernet interface is not enabled, this ifconfig shows your loopback (lo) and bluetooth (pan0).

Try pinging your loopback addres of 127.0.0.1
(This will prove that the network card and the TCP/IP stack are working)

And then try running the folowing commands from the terminal, without the hash(#) symbol, and look for a line with contains 'Ethernet controller' 
#lspci
#lsusb

If you could post the relevant output up then this should show us that the hardware has been detected and tell us what it is so we can work from there.

varspare

---

### Post by a2l007 on 2010-06-12
> **varspare said:**
> Your ethernet interface is not enabled, this ifconfig shows your loopback (lo) and bluetooth (pan0).

Try pinging your loopback addres of 127.0.0.1
(This will prove that the network card and the TCP/IP stack are working)

And then try running the folowing commands from the terminal, without the hash(#) symbol, and look for a line with contains 'Ethernet controller' 
#lspci
#lsusb

If you could post the relevant output up then this should show us that the hardware has been detected and tell us what it is so we can work from there.

varspare

I'm able to successfully ping 127.0.0.1. This is an entry in lspci output related to the ethernet controller. The followig is the output.


lspci 04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)

But i havent found anything relevant in lsusb output which is as follows:
lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 413c:8160 Dell Computer Corp. 
Bus 001 Device 008: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 007: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 006: ID 0c45:6461 Microdia 
Bus 001 Device 005: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by varspare on 2010-06-13
> **a2l007 said:**
> lspci 04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)

It looks like someone else has had the same issue as you, try the steps Pytheas22 mentions in this thread [http://ubuntuforums.org/showthread.php?p=9449490 ]("http://ubuntuforums.org/showthread.php?p=9449490")

Run the diagnostics that Pytheas22 requests first, if you're seeing similar ouput i.e. no mention of the eth0 interface then try his solution which involves downloading a driver.

good luck

varspare

---

### Post by a2l007 on 2010-06-14
> **varspare said:**
> It looks like someone else has had the same issue as you, try the steps Pytheas22 mentions in this thread [http://ubuntuforums.org/showthread.php?p=9449490 ]("http://ubuntuforums.org/showthread.php?p=9449490")

Run the diagnostics that Pytheas22 requests first, if you're seeing similar ouput i.e. no mention of the eth0 interface then try his solution which involves downloading a driver.

good luck

varspare

Hey thanks!!!!! 
I've followed the instructions in that thread and finally i'm able to access internet. Thanks for helping. Actually, i wouldnt have created a new thread if i'd seen this earlier..:p

Cheers

---

### Post by mike909 on 2010-08-26
> **a2l007 said:**
> Hey thanks!!!!! 
I've followed the instructions in that thread and finally i'm able to access internet. Thanks for helping. Actually, i wouldnt have created a new thread if i'd seen this earlier..:p

Cheers
Are you actually able to get both wired (atheros) interface and wireless (broadcom) interface to work at the same time? I have the same laptop, and when I get the wired interface working, according to the "compat-wireless" driver way in that thread, it breaks the wireless interface. I can't get wired and wireless both working at same time, can you?

---

### Post by mike909 on 2010-08-30
Got them both working. For anyone interested, my post about exactly how is at:
[http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9)

---


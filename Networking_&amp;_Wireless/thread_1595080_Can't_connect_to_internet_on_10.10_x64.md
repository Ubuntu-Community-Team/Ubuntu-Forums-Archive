---
title: "Can't connect to internet on 10.10 x64"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by srinurockz on 2010-10-12
I've installed ubuntu 10.10 dual booting with win 7. My internet connection is Direct DSL wired line to my modem. I dont have any wireless connections. 

I'm **unable to connect to my wired connection** and i'm looking for a help to solve it.

I even got connected using live CD of Ubuntu and after my installation too I got connected for the first time, very well without any problems. But eventually after updating my system using update manager and then reboot I couldn't get a connection. 

Even now, just using my live CD I can connect to internet.. but not with the actually Ubuntu Installed.

Maybe this info can be helpful

**ifconfig -a** output 
```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:87:74:dc  
          inet6 addr: fe80::219:d1ff:fe87:74dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120 (120.0 B)  TX bytes:4865 (4.8 KB)
          Interrupt:20 Memory:52200000-52220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

**sudo lshw -C network** output
```
*-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:87:74:dc
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=1.1-0 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:52200000-5221ffff memory:52224000-52224fff ioport:20c0(size=32)
```

**sudo dhclient eth0** output
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:19:d1:87:74:dc
Sending on   LPF/eth0/00:19:d1:87:74:dc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


Any help is greatly appreciated :)

---

### Post by srinurockz on 2010-10-13
anyone got any suggestions for this?

---

### Post by johnnytm on 2010-10-13
eth0 is generally the wired connection. Doesn't look like u have wireless installed. Connect the wired connection and use system-->administration-->additional drivers to check for available wireless drivers. in fact your *network output confirms only an ethernet interface installed.

---

### Post by srinurockz on 2010-10-13
> **johnnytm said:**
> eth0 is generally the wired connection. Doesn't look like u have wireless installed. Connect the wired connection and use system-->administration-->additional drivers to check for available wireless drivers. in fact your *network output confirms only an ethernet interface installed.

Sorry, for the ambiguity !! I'm looking to connect to my wired connection. Now I've mentioned in my opening post, I'm **unable to connect to my wired** connection. 

And yes, there is NO wireless connection in my system nor I want it.

I'm just looking for a help on my wired connections settings.

---

### Post by Huntly on 2010-10-18
Wondering if you've been able to solve this; having the same issue myself.  I'm having to unplug/power off the DSL modem for the connection to be reestablished.

---

### Post by mpcusack on 2010-10-19
Same issue here too. With it not working even on the livecd I was starting to think my port died. Also an intel ethernet chip.

---

### Post by boydude on 2010-10-20
me three.

---

### Post by srinurockz on 2010-10-20
> **Huntly said:**
> Wondering if you've been able to solve this; having the same issue myself.  I'm having to unplug/power off the DSL modem for the connection to be reestablished.

No Buddy, I didn't able to solve this issue. Because nobody here cares to address my issue. I've even tried Launchpad, check my post at [launchpad]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/129251") too.

Well, I'll try unplug/power off my DSL modem next time (It is way better than restarting my whole system).



> **mpcusack said:**
> Same issue here too. With it not working even on the livecd I was starting to think my port died. Also an intel ethernet chip.

Welcome to party mate :(


> **boydude said:**
> me three.

I guess I'm not alone at least !! 


It's been almost one week since I've posted this and yet I'm facing same problem with no improvement.

---

### Post by khanggle on 2010-12-17
Even though there's nothing wrong with my ethernet cord, using another ethernet cord seems to have fixed my problem.

---


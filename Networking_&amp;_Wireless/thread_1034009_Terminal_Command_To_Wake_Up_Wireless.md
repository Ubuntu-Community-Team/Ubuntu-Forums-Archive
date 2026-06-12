---
title: "Terminal Command To Wake Up Wireless?"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by ToyotaGuy23 on 2009-01-07
Hello UF!

What is a terminal command that I can use to 'jumpstart' my wireless card when it doesn't initialize on startup?

Sometimes my wireless seems disabled upon startup.  I would say 20% of the time this problem occurs.  It is fixed with a restart.  

See, usually when I boot, I have a popup at the top letting me know 'wireless networks are available.'  When this problem occurs, I don't get that window, and if I click on the network (two computers) at the top, there are no wireless networks shown.

---

### Post by ToyotaGuy23 on 2009-01-07
DELL Inspiron 1721
2.0 Ghz AMD
2 GB DDR 2
250 GB HD
Dell 1505 802.11 n 
Broadcom 4328 10/100
Ubunutu 8.10 Intrepid

---

### Post by ToyotaGuy23 on 2009-01-07
Also when this happns iwconfig shows 

'no wireless extensions' for evbrything.

but only when the problem happens, and a restart almost always fixes it.

---

### Post by blackened on 2009-01-07
You might try
```
sudo ifconfig **wlan0** up
```
replacing the bold with your interface name (if it is other than wlan0 of course).

---

### Post by ToyotaGuy23 on 2009-01-09
OK the problem just happened. 

I ran ```
iwconfig
``` and got:

lo     no wireless extensions
eth0   no wireless extensions
pan0   no wireless extensions

I then ran ```
sudo ifconfig wlan0 up 
```as suggested and got:  

wlan0:  Error while getting interface flags:  No such device

What is happening? 
What should I do?  
Remember a restart ALWAYS fixes the issue.

---

### Post by kevdog on 2009-01-10
can you list

lshw -C network
ifconfig


Thanks.

---

### Post by ToyotaGuy23 on 2009-01-10
Sure.  Here are my results.  
Please keep in mind that since this is an intermittent problem, the results below are from my system right now.  Let me know if you need these results while it's not working.  
[B]
lshw -C network[/B]
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 03
       serial: 00:1e:4c:77:f8:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. ip=192.168.1.106 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:af:31:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:00:56:ba:9f:83
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[B]
ifconfig[/B]

eth0      Link encap:Ethernet  HWaddr 00:1d:09:af:31:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1192 (1.1 KB)  TX bytes:1192 (1.1 KB)

**wlan0**     Link encap:Ethernet  HWaddr 00:1e:4c:77:f8:a0  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe77:f8a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:314652 (314.6 KB)  TX bytes:58573 (58.5 KB)
          Interrupt:17 Memory:fe8fc000-fe900000 


PLEASE NOTE:  When the network does NOT start, I have no 'wlan0' 
So I guess 'wlan0' to work, so we can get the ball rolling.  

I use the IRC channel, and I bought a book today, I'm really trying, so please have some newbie patience!  =)

---


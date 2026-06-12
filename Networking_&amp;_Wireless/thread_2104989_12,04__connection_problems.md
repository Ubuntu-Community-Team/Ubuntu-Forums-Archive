---
title: "12,04  connection problems"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by MontrealCorp on 2013-01-14
hi, has more time pass, more difficulty happens wich i find strange.
 
i run ubuntu 12.04 , and now, each time i restart my computer, my internet connection cannot be started unless i shut down the router completely.
 
i use belkin usb N wireless 
 
when i first srat use ubuntu couple weeks ago, i never had this problem.
but after a couple of format and install in the past few weeks, now i just cant connect to the internet without a shut down of the router anymore.
 
strange thing is, all the latop in the house (2) works without this problem, iphone wifi works great as well and never need a shutdown from the router to make them work.
 
what is going on ?
why is shutting down the router only for my desktop ubuntu 12.04 is needed that much to accces internet ?
especially when it was not even need it before ?
 
ty

---

### Post by ahallubuntu on 2013-01-14
Please tell us exactly which Belkin card you are using.

Also, open Terminal and in it type a few commands and please provide the output:

```
sudo lshw -C network
iwconfig
```

---

### Post by MontrealCorp on 2013-01-14
it is a belkin N wireless adapter  # F5D8053 v3

sorry for late response, i was in the process of going for a reformat again trying this time to install ubuntu without an internet connection in case of w.e miracle this could change anything ...?

now i am sending the info i was able to do with  my internet WIRED connection from my iphone o0....


ty for help btw...:)



  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:23:54:5d:3a:94
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:23 memory:f9f7c000-f9f7cfff ioport:c480(size=8) memory:f9f7e400-f9f7e4ff memory:f9f7e000-f9f7e00f
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 00:1c:df:2f:7a:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-35-generic-pae firmware=0.29 link=yes multicast=yes wireless=IEEE 802.11bgn
simon@DesktopOffice:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

simon@DesktopOffice:~$

---

### Post by MontrealCorp on 2013-01-15
Bump ?

Btw , i dont think it is my usb adapter cause he see all the wireless network available including the one i should connect too.
It just does not seem to registered while all my other laptop, iphone, etc connect without any problem and no need to shutdown the router to make them work as well, strange.

I just do not see why it is not working when couple weeks ago it was working flawlessly , it is a fresh install has well .
Ty

---

### Post by MontrealCorp on 2013-01-15
after seing nohting could be done and some laptops started to fall apart with bad connection i simply reset to factory the router and i change evryhting for wireless connection.

now it works , dunno what happen but has long it is working :)...

---


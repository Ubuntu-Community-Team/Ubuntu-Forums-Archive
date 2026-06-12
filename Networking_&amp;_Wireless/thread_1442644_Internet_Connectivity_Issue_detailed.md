---
title: "Internet Connectivity Issue: detailed"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Ryuzog on 2010-03-30
dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.

out of these I have no idea what I'm using, I buy a card, company is China Unicom, I am in China, cards come in speeds of 2M and 4M,EDIT: they also have limits,there are 50hr cards,1 month cards, 1 half-year cards, and year cards. Vista at least, prompts to disconnect after 20 mins of inactivity. Some sort of dial up? I've been asking for broadband help, searched dial-up and broadband and there seems to be a hybrid dialup broadband called ..diaup broadband...
login is f2009101600084534, pass is 8 digits long.

My translation of the top of the card says: High Speed Campus Broadband Internet card. Could be high speed dialup, which I hear is also known as broadband dialup. On my XP system, it shows the keywords: pppoe, dialup, and broadband when I try to connect.

```

lspci
lsusb
lshw -class network
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```

both pings are unreachable

```
 *-network               

       description: Wireless interface

       product: AR5001 Wireless Network Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: wmaster0

       version: 01

       serial: 00:26:5e:2f:d6:1e

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg

       resources: irq:16 memory:55100000-5510ffff

  *-network

       description: Ethernet interface

       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter

       vendor: Attansic Technology Corp.

       physical id: 0

       bus info: pci@0000:03:00.0

       logical name: eth0

       version: c0

       serial: 00:23:5a:f1:3c:f9

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 multicast=yes

       resources: irq:27 memory:53000000-5303ffff ioport:1000(size=128)


eth0      Link encap:Ethernet  HWaddr 00:23:5a:f1:3c:f9  

          inet6 addr: fe80::223:5aff:fef1:3cf9/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:20979712 errors:0 dropped:0 overruns:0 frame:0

          TX packets:9 errors:0 dropped:0 overruns:0 carrier:2

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)

          Interrupt:27 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2f:d6:1e  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-2F-D6-1E-00-00-00-00-00-00-00-00-00-00  

          UP RUNNING  MTU:0  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr 00:23:5a:f1:3c:f9  

          inet6 addr: fe80::223:5aff:fef1:3cf9/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:20979712 errors:0 dropped:0 overruns:0 frame:0

          TX packets:9 errors:0 dropped:0 overruns:0 carrier:2

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)

          Interrupt:27 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2f:d6:1e  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-2F-D6-1E-00-00-00-00-00-00-00-00-00-00  

          UP RUNNING  MTU:0  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0      Link encap:Ethernet  HWaddr 00:23:5a:f1:3c:f9  

          inet6 addr: fe80::223:5aff:fef1:3cf9/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:20979712 errors:0 dropped:0 overruns:0 frame:0

          TX packets:9 errors:0 dropped:0 overruns:0 carrier:2

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:1494 (1.4 KB)

          Interrupt:27 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2f:d6:1e  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-2F-D6-1E-00-00-00-00-00-00-00-00-00-00  

          UP RUNNING  MTU:0  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

tried inputing login and pass in dsl leaving "service" blank.
tried sudo pppoeconf, did not work, plog said network was unreachable.

Wireless connection does work,

Posted from Vista Computer

Had a previous post.

---

### Post by dineshs on 2010-03-30
please explain whether you have a modem,if so how it is connected to the PC?I mean ethernet/usb/serial port /wireless

---

### Post by Ryuzog on 2010-03-30
I'm in a dorm room, I connect a wire from my computer to the wall, the end of the wires are like fat stepped pyramids, the same for phones I think.

---

### Post by Ryuzog on 2010-03-31
=/

I think it's a general problem actually, regular ubuntu and mint seem to also have it.

I think it's just a fast dial up.

---

### Post by dineshs on 2010-04-01
Pl confirm what socket it is .I mean RJ 11 or RJ 45.I dont think 2M/4M speed is attainable via dialup.

---

### Post by Ryuzog on 2010-04-01
? I don't understand

---

### Post by dineshs on 2010-04-01
RJ 11 is normally used for connecting a telephone.It is small max 4 conductors
RJ 45 is ethernet/lan connector .pl see attachment

---


---
title: "2x gigabit ethernet on single PC, both connect 100 mbit"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Huufarted on 2009-04-01
I have a small fileserver.  It's just used for myself and my wife for convenience.  It's also used as a media server for our television.

I'm running it with Ubuntu 8.10 (Intrepid) on it.

It's running an Intel Atom motherboard as shown here:

D945GCLF2
[http://www.intel.com/Products/Desktop/Motherboards/D945GCLF2-D945GCLF2D/D945GCLF2-D945GCLF2D-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/D945GCLF2-D945GCLF2D/D945GCLF2-D945GCLF2D-overview.htm)

The product spec sheet says the following about the on-board NIC:

> 
The LAN, based on the RealTek RTL8111C Ethernet Controller, provides the following 
functions:   10/100/1000 Mb/s Gigabit Ethernet LAN


I also tossed on a gigabit NIC as shown here:

NetGear GA311 Ver.A1
[http://kb.netgear.com/app/products/model/a_id/2432](http://kb.netgear.com/app/products/model/a_id/2432)

Both of these NICs connect ONLY at 100 mbit and I don't know why.  At first the secondary NIC was connecting at gig speed.  The motherboard network interface I'm not sure of at the start because it was only connected to a 100 mbit device on the other side.

The Netgear is connected to a Netgear 5 port gig switch.  The switch has 2 indicator LEDs where if one LED is lit, it's 100 mbit.  If both are lit, it's 1 gbit connection.

Transfer speeds originally were at 50 MB/sec when it was up on gigabit, limited only by the hard drive in the machine.

Transfer speeds with 100 mbit are as expected, 10-12 MB/sec.

The motherboard interface is using a Realtek RTL8111C chip.

The Netgear NIC uses a Realtek RTL8169 chip.

Can someone help me get these network interfaces connecting at gig speeds?

---

### Post by Huufarted on 2009-04-02
New information!

I can use the below command after a reboot and it will switch to gigabit speeds.....  for awhile.  Once it switches back to 100 mbit, if I try to use ethtool again, it takes a few seconds for the NIC to come back on, but when it does, it's still sitting there at 100 mbit.

```
sudo ethtool -s eth1 speed 1000 duplex full
```

---

### Post by Huufarted on 2009-04-03
Any ideas?  I cannot force it into gigabit, even though I'm using cat6 cables (have tried multiple cables), it's a gigabit switch, and a gigabit NIC.

---


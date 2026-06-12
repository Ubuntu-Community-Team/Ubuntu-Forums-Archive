---
title: "Problem with sky2 driver with  marvell  88e8050"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by banchoff on 2009-11-05
Hello, 
  I'm having a problem with a network card Marvell 88E8050 in a production server.

The problem is the following:
Randomly -but after a heavy load- the link disables and then enables again. If I run "dmesg", I see this:
---------------------------------------------------------------------------------
[2390733.469584] sky2 eth1: Link is up at 1000 Mbps, full duplex, flow control rx
[2393968.736883] sky2 eth1: hung mac 124:94 fifo 195 (80:75)
[2393968.736890] sky2 eth1: receiver hang detected
[2393968.737397] sky2 eth1: disabling interface
[2393968.737714] sky2 eth1: enabling interface
[2393971.918659] sky2 eth1: Link is up at 1000 Mbps, full duplex, flow control rx
[2745178.359470] sky2 eth1: hung mac 124:80 fifo 195 (18:13)
[2745178.359478] sky2 eth1: receiver hang detected
[2745178.359963] sky2 eth1: disabling interface
[2745178.360254] sky2 eth1: enabling interface
[2745181.447281] sky2 eth1: Link is up at 1000 Mbps, full duplex, flow control rx
---------------------------------------------------------------------------------

The network card is (lspci):
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 18)

I've read some posts in other forums, but it doesn't seem to be the same problem other people report, because in their case the machine hangs, while in this case it seems the driver "resets" and continues running. Besides, they report the problem with a different netcard model (88E8053).

If I run a ping flood, eventually the problem appears (I see those messages issuing "dmesg"), but there is no loss of connectivity.

The machine is an ubuntu Hardy with kernel 2.6.24-24-server. Running ifconfig, I get some dropped packets:
-------------------------------------------------------------------------------------------
~$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:0e:0c:3c:a2:a9  
          inet addr:192.168.5.2  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe3c:a2a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1841720369 errors:16 dropped:16 overruns:0 frame:16
          TX packets:980407497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2223174614 (2.0 GB)  TX bytes:2018466053 (1.8 GB)
          Interrupt:16 
--------------------------------------------------------------------------------------------

Thanks!

---


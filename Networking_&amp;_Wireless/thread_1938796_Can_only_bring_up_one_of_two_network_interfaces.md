---
title: "Can only bring up one of two network interfaces"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by mstaessen on 2012-03-10
Hi there!

I'm having a bizarre issue with my HP Proliant DL 360 G4p server. It has two gigabit ethernet interfaces but I can bring up only one of them. This is starting to freak me out and that's why I turned here. I'm running the x64 ubuntu 11.10 server edition. 

lshw -c network shows that the second interface is disabled. I have no idea why ans how to enable it. 

```

mstaessen@mist-server:~$ sudo lshw -c network
  *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:18:71:e3:6d:26
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5704-v3.27b, ASFIPMIc v2.36 ip=10.48.8.71 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:25 memory:fdf70000-fdf7ffff
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2.1
       bus info: pci@0000:02:02.1
       logical name: eth1
       version: 10
       serial: 00:18:71:e3:6d:25
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=5704-v3.27b latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:26 memory:fdf60000-fdf6ffff

```

If I try to ifup eth1, then I get
```

mstaessen@mist-server:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.

```

I figured that's what happens when there is no eth1 listed in /etc/network/interfaces. But when I add the configuration for eth1, I still can't ifup.

```

mstaessen@mist-server:~$ sudo ifup eth1
RTNETLINK answers: File exists
Failed to bring up eth1.

```

I've also tried ifconfig eth1 up but without any result.

I really need some help fixing this. It's driving me crazy. Thanks.

---

### Post by josephmills on 2012-03-10
Could we see a 
```
dmesg | grep tg3
``` 
thanks

---

### Post by mstaessen on 2012-03-10
Sure, 

```

 dmesg | grep tg3
[    1.124039] tg3.c:v3.119 (May 18, 2011)
[    1.124093] tg3 0000:02:02.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    1.186281] tg3 0000:02:02.0: eth0: Tigon3 [partno(349321-001) rev 2100] (PCIX:66MHz:64-bit) MAC address XX:XX:XX:XX:XX:XX
[    1.186287] tg3 0000:02:02.0: eth0: attached PHY is 5704 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.186291] tg3 0000:02:02.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    1.186295] tg3 0000:02:02.0: eth0: dma_rwctrl[769f0000] dma_mask[64-bit]
[    1.186365] tg3 0000:02:02.1: PCI INT B -> GSI 26 (level, low) -> IRQ 26
[    1.298549] tg3 0000:02:02.1: eth1: Tigon3 [partno(349321-001) rev 2100] (PCIX:66MHz:64-bit) MAC address XX:XX:XX:XX:XX:XX
[    1.298554] tg3 0000:02:02.1: eth1: attached PHY is 5704 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.298557] tg3 0000:02:02.1: eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.298561] tg3 0000:02:02.1: eth1: dma_rwctrl[769f0000] dma_mask[64-bit]
[   11.528132] tg3 0000:02:02.0: eth0: Link is up at 100 Mbps, full duplex
[   11.528139] tg3 0000:02:02.0: eth0: Flow control is off for TX and off for RX
[ 1030.336007] tg3 0000:02:02.1: eth1: Link is up at 100 Mbps, full duplex
[ 1030.336014] tg3 0000:02:02.1: eth1: Flow control is off for TX and off for RX

```

Apologies for the slow response

---

### Post by josephmills on 2012-03-10
could we see a 
```
lsmod  
```

thanks

---

### Post by mstaessen on 2012-03-10
Whatever helps me solve this mystery :)

```

$ lsmod
Module                  Size  Used by
vesafb                 13809  1
psmouse                73882  0
hpilo                  17399  0
serio_raw              13166  0
shpchp                 37345  0
e752x_edac             18564  0
edac_core              53746  1 e752x_edac
lp                     17799  0
parport                46562  1 lp
tg3                   147729  0
cciss                 110804  3
floppy                 70365  0

```

---

### Post by josephmills on 2012-03-10
Ok so this is what I am seeing you have to cards that run off the same driver. they could be getting in the way of each other but I am not sure you could try to unplug the ethernet cable then rmmod tg3  then plug in ethernet cable into 2nd port and then modprobe tg3  then try to bring it up. If that dont work I am out of ideas I hope you get it sorted.

---

### Post by mstaessen on 2012-03-10
Didn't work. Tried to replace the driver (tg3-3.119) with the one from the broadcom website (tg3-3.122g) but without result. 

If I bring down eth0 and then bring up eth1 (which works then), the 'DISABLED' disappears, but I get the RTNETLINK answer when bringing up eth0.

The driver is somehow preventing use of both NIC ports... very annoying

---

### Post by mstaessen on 2012-03-10
I found the solution. There were two gateways defined in /etc/network/interfaces while you simple can't have more then one gateway. It actually makes no sense either.

If you would have two gateways, your routing table would have a double entry for dest 0.0.0.0. The double route is what causes the RTNETLINK answer "File exists", meaning there is already a route for 0.0.0.0.

I've commented out one of the gateways and now I can ifup both eth0 and eth1.

Now I only need another route for the traffic on the internal interface.

---


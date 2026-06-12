---
title: "Wired network not working after upgrade"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by orkybash on 2009-04-23
Just did an in-place upgrade to Jaunty, and my wired network broke.

I am an idiot when it comes to networking on linux, so I have no idea what info to give or what to check.

Help?

---

### Post by Ryuhayabusa on 2009-04-23
try following the instructions in the sticky "how to post a wireless ticket" thread.

that way someone knowledgable will be able to help you.

---

### Post by orkybash on 2009-04-23
Sorry, didn't read that because my problem is not with wireless.

---

### Post by orkybash on 2009-04-23
I don't have a memory stick so I can't get the output of these commands until tomorrow :( I'll bump this then.

Thanks.

---

### Post by orkybash on 2009-04-23
Someone saved me!

The computer is a dell, but I can't get more specific than that (school-provided)

The card is a Broadcom Corp etXtreme BCM5751 Gigabit Ethernet PCE Express.  It's an integrated chipset, just judging from where I put the cable ;)

Some more command output follows....

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:57:89:aa
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14004 (14.0 KB)  TX bytes:14004 (14.0 KB)

partial dmsg (the parts that seem to pertain to eth0):
[    5.520909] eth0: Tigon3 [partno(BCM5751PKFBG) rev 4001 PHY(5750)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:14:22:57:89:aa
[    5.520914] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.520917] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]

[   59.767808] Uhhuh. NMI received for unknown reason b1 on CPU 0.
[   59.767808] You have some hardware problem, likely on the PCI bus.
[   59.767808] Dazed and confused, but trying to continue
[   61.165609] tg3: eth0: No firmware running.
[   71.712712] ADDRCONF(NETDEV_UP): eth0: link is not ready

lshw -C network:

  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:57:89:aa
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.44a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:b7:29:76:79:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by orkybash on 2009-04-24
On further investigation it seems that there are no network devices listed in /dev at all!! 

Anyone?  Please help, I'm really desperate!!!!!

---

### Post by jkwuc89 on 2009-04-28
I have the same wired network configuration on my HP Workstation xw6200.  After upgrading from 8.10 to 9.04 and rebooting, my network was down.  I rebooted again without changing anything and this time, the network came up just fine under 9.04.

---

### Post by ScottCh on 2009-05-04
you may find this helpful, not sure.  I did a two-stage upgrade from Hardy to Jaunty.  After completing the upgrade my wired network would not work.  The network icon showed a red X on its lower right.

First,  I followed the advice of others and commented out my ethernet device (now eth2 for some reason) from /etc/network/interfaces.  But after rebooting,  I still was not able to reach my router by pinging its IP address, ping just said that sendmsg was not permitted.  I could ping localhost and my system's IP successfully.  

I had ufw disabled, but iptables turned out to be locking down every external address.

If you need iptables, DO NOT DO THIS.  I have a NAT router protecting my lan.

Softer gobs of experimentation, what I found was that flushing EVERYTHING out of iptables re-activated my wired networking.

[INDENT]sudo iptables --flush
sudo iptables -t filter --flush
sudo iptables -t nat --flush
sudo iptables -t mangle --flush
sudo iptables -t raw --flush[/INDENT]

I have no idea why iptables had my network totally shut down following my upgrade.  I've upgraded this machine starting with breezy badger, and this is completely new.

Scott C. in Cary, NC USA

---


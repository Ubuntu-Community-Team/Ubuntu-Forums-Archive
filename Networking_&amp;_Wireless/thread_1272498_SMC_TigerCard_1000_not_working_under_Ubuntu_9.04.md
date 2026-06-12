---
title: "SMC TigerCard 1000 not working under Ubuntu 9.04"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by dqqdrake on 2009-09-22
I'm adding a SMC TigerCard 1000 (PCI 64bit GbE card) to a Dell PowerEdge 1550.  The server is running Ubuntu 9.04.  The card seems to be recognized by the O/S fine.  The tg3 driver is loaded.  After I updated /etc/network/interfaces and restarted networking, ifconfig shows eth2 is up and running.  However I just couldn't ping any host on the same subnet - getting "destination host unreachable".  Nothing seems to be out of the ordinary.  dmesg shows no sign of error (see below).  The "Link is down" was the moment I unplugged the cable to see if it would respond to that.

user@vmware3:~$ dmesg | grep eth2
[I][    5.778166] eth2: Tigon3 [partno(AC91001A1) rev 0105 PHY(5701)] (PCI:66MHz:64-bit) 10/100/1000Base-T Ethernet 00:04:e2:35:10:13
[    5.778179] eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[0]
[    5.778186] eth2: dma_rwctrl[76ff000f] dma_mask[64-bit]
[ 4934.739445] ADDRCONF(NETDEV_UP): eth2: link is not ready
[ 5298.861278] tg3: eth2: Link is up at 1000 Mbps, full duplex.
[ 5298.861287] tg3: eth2: Flow control is on for TX and on for RX.
[ 5298.862060] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[ 5309.670015] eth2: no IPv6 routers present
[ 9471.433471] tg3: eth2: Link is down.
[ 9491.789206] tg3: eth2: Link is up at 1000 Mbps, full duplex.
[ 9491.789215] tg3: eth2: Flow control is on for TX and on for RX.
[10211.181041] ADDRCONF(NETDEV_UP): eth2: link is not ready
[10213.623330] tg3: eth2: Link is up at 1000 Mbps, full duplex.
[10213.623339] tg3: eth2: Flow control is on for TX and on for RX.
[10213.624120] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[10223.710018] eth2: no IPv6 routers present[/I]

I have no iptables rule set up; default is ACCEPT.  

The only thing I found strange is that under ifconfig the byte counts for the interface never seem to go up but the packet counts do.  

eth2      Link encap:Ethernet  HWaddr 00:04:e2:35:10:13
          inet addr:10.1.100.56  Bcast:10.1.100.255  Mask:255.255.255.0
          inet6 addr: fe80::204:e2ff:fe35:1013/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:128 (128.0 B)  TX bytes:236 (236.0 B)
          Interrupt:29

So if I keep pinging, the "RX packets:118" and "TX packets:42" will continue to go up, but "RX bytes" and "TX bytes" never pass a few hundred bytes, and sometimes one of them is 0.  It's almost like the counters are constantly resetting.  Also for eth0 there's no interrupt # listed (eth2 is 29).  Don't know if that's an issue.

Where do I need to look?  Thanks!

---

### Post by dqqdrake on 2009-09-23
Just had a kernel panic (see screenshot).  Looks it's something with tg3 on interrupt.  Anyone knows where I can find people who knows the internals of the tg3 module?

---

### Post by dqqdrake on 2009-09-25
I ended up using a TrendNet card, using *r8169* module.  It's a 32-bit card but it'll have to make do for now even though I'd really like something that's 64bit with some kind of processing assistance (TigerCard has checksum offload).  Before that I tried a Zyxel 64bit I have for spare.  That gave me a "P&P configuration error: unknown device" upon booting.  BTW, someone mentioned *irqbalance* causing trouble with tg3.  That's on a FC8.

---


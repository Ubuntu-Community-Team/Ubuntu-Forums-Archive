---
title: "Can't get BCM5716 working"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by boppen on 2010-08-17
Hi!
 
I have a Dell R210 with Broadcom NetXtremeII 5716 NIC's (bnx2 module) but I can't get them working, It's a newly installed 10.04 Server with 2.6.32, amd64.
The NIC's are detected but they never receives any data - they only sends. I have tried both NIC's, different patch cables, different switches but always with the same result :-(
Is there anyone that have a hint what might be wrong?!
 
dmesg;
```
[   25.775860] Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.0.8e (April 13, 2010)
[   25.775879] bnx2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.775886] bnx2 0000:02:00.0: setting latency timer to 64
[   25.776739] bnx2 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   25.776744] bnx2 0000:02:00.1: setting latency timer to 64
[  135.331308] bnx2: eth0 NIC Copper Link is Up, 100 Mbps full duplex
[  478.191014] bnx2: eth0 NIC Copper Link is Down
[  516.327851] bnx2: eth0 NIC Copper Link is Up, 100 Mbps full duplex
```
 
ifconfig:
```
 
eth0      Link encap:Ethernet  HWaddr 00:26:b9:76:b7:5a
          inet6 addr: fe80::226:b9ff:fe76:b75a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:150995 dropped:0 overruns:0 frame:150995
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:6904 (6.9 KB)
          Interrupt:16 Memory:da000000-da012800

```
 
As you can see there are lot's of errors but no RX?
 
Thanks for any help, regards Boppen!

---


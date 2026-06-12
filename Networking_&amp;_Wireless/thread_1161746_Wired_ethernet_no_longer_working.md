---
title: "Wired ethernet no longer working"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by mingtien on 2009-05-17
I've encountered a problem with wired ethernet, and am wondering if I could enlist someone's help to arrive at a solution.

Most days, I use wireless broadband (EVDO/CDMA) which works beautifully under Jaunty, but about 2-3 times a month, I go to an Internet cafe to run Update Manager (EVDO is fast enough for most things, including grabbing some fairly huge files, but too slow for Synaptic).  This time round, eth0 would not connect (retry in Network Manager -- connects for a few seconds and then disconnects).  I've been using Jaunty since 24 April, with no networking problems thus far.

Could I trouble someone with a bit more networking knowledge than me to  have a look at the evidence below, and please let me know if I am missing something blatantly obvious?

Error messages:

```


May 17 11:34:08 buriram dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 17 11:34:08 buriram dhclient: 
May 17 11:34:08 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:34:08 buriram NetworkManager: <info>  dhclient started with pid 4162 
May 17 11:34:08 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 17 11:34:08 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:34:08 buriram NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May 17 11:34:08 buriram dhclient: Listening on LPF/eth0/00:19:db:39:ab:25
May 17 11:34:08 buriram dhclient: Sending on   LPF/eth0/00:19:db:39:ab:25
May 17 11:34:08 buriram dhclient: Sending on   Socket/fallback
May 17 11:34:09 buriram postfix/master[2928]: reload configuration /etc/postfix
May 17 11:34:11 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 17 11:34:15 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 17 11:34:22 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
May 17 11:34:33 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
May 17 11:34:54 buriram NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
May 17 11:34:54 buriram NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 4162 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
May 17 11:34:54 buriram NetworkManager: <info>  (eth0): device state change: 7 -> 9 
May 17 11:34:54 buriram NetworkManager: <info>  Marking connection 'Wired connection 1' invalid. 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) failed. 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
May 17 11:34:54 buriram NetworkManager: <info>  (eth0): device state change: 9 -> 3 
May 17 11:34:54 buriram NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May 17 11:34:54 buriram NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 17 11:34:54 buriram NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 17 11:34:54 buriram NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 17 11:34:54 buriram dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 17 11:34:54 buriram dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 17 11:34:54 buriram dhclient: All rights reserved.
May 17 11:34:54 buriram dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 17 11:34:54 buriram dhclient: 
May 17 11:34:54 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:34:54 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:34:54 buriram NetworkManager: <info>  dhclient started with pid 4210 
May 17 11:34:54 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 17 11:34:54 buriram NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May 17 11:34:54 buriram dhclient: Listening on LPF/eth0/00:19:db:39:ab:25
May 17 11:34:54 buriram dhclient: Sending on   LPF/eth0/00:19:db:39:ab:25
May 17 11:34:54 buriram dhclient: Sending on   Socket/fallback
May 17 11:34:57 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 17 11:35:03 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 17 11:35:12 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 17 11:35:25 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 17 11:35:38 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
May 17 11:35:40 buriram NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
May 17 11:35:40 buriram NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 4210 
May 17 11:35:40 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 17 11:35:40 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
May 17 11:35:40 buriram NetworkManager: <info>  (eth0): device state change: 7 -> 9 
May 17 11:35:40 buriram NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
May 17 11:35:40 buriram NetworkManager: <info>  Activation (eth0) failed. 
May 17 11:35:40 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
May 17 11:35:40 buriram NetworkManager: <info>  (eth0): device state change: 9 -> 3 
May 17 11:35:40 buriram NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) starting connection 'Cafe' 
May 17 11:35:42 buriram NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 17 11:35:42 buriram NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 17 11:35:42 buriram NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 17 11:35:42 buriram dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 17 11:35:42 buriram dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 17 11:35:42 buriram dhclient: All rights reserved.
May 17 11:35:42 buriram dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 17 11:35:42 buriram dhclient: 
May 17 11:35:42 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:35:42 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:35:42 buriram NetworkManager: <info>  dhclient started with pid 4229 
May 17 11:35:42 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 17 11:35:42 buriram NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May 17 11:35:42 buriram dhclient: Listening on LPF/eth0/00:19:db:39:ab:25
May 17 11:35:42 buriram dhclient: Sending on   LPF/eth0/00:19:db:39:ab:25
May 17 11:35:42 buriram dhclient: Sending on   Socket/fallback
May 17 11:35:46 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 17 11:35:48 buriram NetworkManager: <info>  (eth0): device state change: 7 -> 3 
May 17 11:35:48 buriram NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
May 17 11:35:48 buriram NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 4229 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) starting connection 'Cafe' 
May 17 11:35:48 buriram NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 17 11:35:48 buriram NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 17 11:35:48 buriram NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 17 11:35:48 buriram dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 17 11:35:48 buriram dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 17 11:35:48 buriram dhclient: All rights reserved.
May 17 11:35:48 buriram dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 17 11:35:48 buriram dhclient: 
May 17 11:35:48 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:35:48 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:35:48 buriram NetworkManager: <info>  dhclient started with pid 4231 
May 17 11:35:48 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 17 11:35:48 buriram NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May 17 11:35:48 buriram dhclient: Listening on LPF/eth0/00:19:db:39:ab:25
May 17 11:35:48 buriram dhclient: Sending on   LPF/eth0/00:19:db:39:ab:25
May 17 11:35:48 buriram dhclient: Sending on   Socket/fallback
May 17 11:35:50 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 17 11:35:55 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 17 11:36:07 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 17 11:36:21 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 17 11:36:29 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 17 11:36:29 buriram NetworkManager: <info>  (eth0): device state change: 7 -> 3 
May 17 11:36:29 buriram NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
May 17 11:36:29 buriram NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 4231 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
May 17 11:36:29 buriram NetworkManager: <info>  (eth0): device state change: 3 -> 4 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 17 11:36:29 buriram NetworkManager: <info>  (eth0): device state change: 4 -> 5 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 17 11:36:29 buriram NetworkManager: <info>  (eth0): device state change: 5 -> 7 
May 17 11:36:29 buriram NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 17 11:36:29 buriram dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 17 11:36:29 buriram dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 17 11:36:29 buriram dhclient: All rights reserved.
May 17 11:36:29 buriram dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 17 11:36:29 buriram dhclient: 
May 17 11:36:29 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:36:30 buriram NetworkManager: <info>  dhclient started with pid 4238 
May 17 11:36:30 buriram NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 17 11:36:30 buriram NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
May 17 11:36:30 buriram dhclient: wmaster0: unknown hardware address type 801
May 17 11:36:30 buriram dhclient: Listening on LPF/eth0/00:19:db:39:ab:25
May 17 11:36:30 buriram dhclient: Sending on   LPF/eth0/00:19:db:39:ab:25
May 17 11:36:30 buriram dhclient: Sending on   Socket/fallback
May 17 11:36:30 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 17 11:36:36 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 17 11:36:50 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 17 11:36:57 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
May 17 11:37:05 buriram dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
May 17 11:37:14 buriram NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
May 17 11:37:15 buriram NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 4238 
May 17 11:37:15 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
May 17 11:37:15 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
May 17 11:37:15 buriram NetworkManager: <info>  (eth0): device state change: 7 -> 9 
May 17 11:37:15 buriram NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
May 17 11:37:15 buriram NetworkManager: <info>  Activation (eth0) failed. 
May 17 11:37:15 buriram NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
May 17 11:37:15 buriram NetworkManager: <info>  (eth0): device state change: 9 -> 3 
May 17 11:37:15 buriram NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
May 17 11:37:15 buriram NetworkManager: <info>  Activation (eth0) starting connection 'Cafe' 


```


Possibly appropriate bits from dmesg:

```


[    3.675307] compcache: Compressed swap size set to: 353692 KB
[    3.675908] TLSF: pool: f7d5d000, init_size=16384, max_size=0, grow_size=16384
[    4.239195] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.239218] r8169 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.239235] r8169 0000:04:00.0: setting latency timer to 64
[    4.239304] r8169 0000:04:00.0: no MSI. Back to INTx.
[    4.239908] eth0: RTL8168b/8111b at 0xf7dd4000, 00:19:db:39:ab:25, XID 38000000 IRQ 19
[    4.329298] ohci1394 0000:05:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.380103] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[ffcff000-ffcff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]

[   30.084327] r8169: eth0: link up
[   30.084348] r8169: eth0: link up
[   30.085409] rt61pci 0000:05:09.0: firmware: requesting rt2561.bin
[   30.192355] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.404027] eth0: no IPv6 routers present
[   57.023841] CPU0 attaching NULL sched-domain.
[   57.024919] CPU0 attaching NULL sched-domain.
[   89.580051] Clocksource tsc unstable (delta = -277749800 ns)
[  417.897255] r8169: eth0: link down


```

ifconfig (sorry running now that I am no longer in the Internet cafe, so TX/RX info will not be the same:


```


eth0      Link encap:Ethernet  HWaddr 00:19:db:39:ab:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49912 (49.9 KB)  TX bytes:49912 (49.9 KB)


```


Thanks very much for any hints or assistance!!!

---

### Post by Peter09 on 2009-05-17
From your output it looks like DHCP failed. Check your router (may be worth a power cycle).

If you have had this working, have you made any recent changes?

---

### Post by mingtien on 2009-05-17
HI Peter,

Thank you for your reply.  It's a router in an Internet cafe, so DHCP is pretty much a requirement (most people come in with their own notebooks, rather than using one of the PC's that are there).  I will try another venue to test this, though.  

Cheers!

David

---

### Post by Iowan on 2009-05-18
See if [this]("http://ubuntuforums.org/showpost.php?p=7280398&postcount=3") one helps.

---


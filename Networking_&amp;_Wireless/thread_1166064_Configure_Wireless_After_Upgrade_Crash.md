---
title: "Configure Wireless After Upgrade Crash"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by brett- on 2009-05-21
I can't figure this one out.  My PC froze while running update manager (I traced the crash to CPU overheating caused by thick dust built up on the heat sink and corrected).  At this point the wireless connection is not working.

**lshw - **

*-network UNCLAIMED
             description: Ethernet controller
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32 maxlatency=28 mingnt=10

**ifconfig - **

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4084 (4.0 KB)  TX bytes:4084 (4.0 KB)

From the live CD the wireless card is detected and all is well.

**lshw - **

*-network
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: wifi0
             version: 01
             serial: 00:11:50:6f:cb:60
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci ip=192.168.0.2 latency=168    maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

**ifconfig - **

ath0      Link encap:Ethernet  HWaddr 00:11:50:6f:cb:60  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1928 (1.9 KB)  TX bytes:3285 (3.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27072 (27.0 KB)  TX bytes:27072 (27.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-50-6F-CB-60-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1114 errors:0 dropped:0 overruns:0 frame:13529
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:92547 (92.5 KB)  TX bytes:14187 (14.1 KB)
          Interrupt:18 

Any kind (or not) hints are welcome?  I dread a re-install.

---

### Post by superprash2003 on 2009-05-21
while booting ( grub ) choose an older kernel and see if that works.

---

### Post by brett- on 2009-05-21
Thanks, that worked. ):P I then edited grub/menu.lst, and set "default" to last good kernel.  Is there a way to remove the offending kernel?

---

### Post by superprash2003 on 2009-05-22
well dont completely remove it , wait for a while and login to that kernel and perform updates , it may get fixed soon

---


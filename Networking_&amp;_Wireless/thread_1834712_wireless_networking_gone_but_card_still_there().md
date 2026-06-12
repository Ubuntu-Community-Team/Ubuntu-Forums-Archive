---
title: "wireless networking gone but card still there(?)"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by eddski on 2011-08-28
my wireless is mia after update, as far as i can tell thats what it was, and i cant get it back. i have added some output from some commands and it looks like my card(intel 3945abg) is still there. ive tried adding nm to the panel but no wireless network detected.
running 10.04 on a toshiba satellite u205.


root is in /home/eddski# ifconfig

eth0      Link encap:Ethernet  HWaddr 00:15:b7:0c:28:57  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:38 errors:0 dropped:0 overruns:0 frame:0

          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:2324 (2.3 KB)  TX bytes:2324 (2.3 KB)



wlan0     Link encap:Ethernet  HWaddr 00:18:de:53:62:b0  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




root is in /home/eddski# iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11abg  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Encryption key:off

          Power Management:off


root is in /home/eddski# lspci|grep work

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)


root is in /home/eddski# lspci -nn |grep 0280

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

hope the output helps, thanks

---

### Post by fdrake on 2011-08-28
can you post the results from the script in the link.

[http://ubuntuforums.org/showthread.php?p=11194893#post11194893](http://ubuntuforums.org/showthread.php?p=11194893#post11194893)

---

### Post by eddski on 2011-08-28
the results from the script are below, thanks for helping me


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++Sysyem-Info+++++++++++++++++++++++++++++++++++++++++++++++
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux eddski-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++
eth0      Link encap:Ethernet  HWaddr 00:15:b7:0c:28:57  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:b7ff:fe0c:2857/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:530597 (530.5 KB)  TX bytes:73031 (73.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2460 (2.4 KB)  TX bytes:2460 (2.4 KB)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000    0     0     0        0      0      0      0      0        0

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lswh+++++++++++++++++++++++++++++++++++++++++++++++++++++
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:53:62:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:26 memory:ffcff000-ffcfffff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:15:b7:0c:28:57
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.13 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:ffaff000-ffafffff ioport:bf40(size=64)

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lspci++++++++++++++++++++++++++++++++++++++++++++++++++++
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at ffaff000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at bf40 [size=64]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: e100
	Kernel modules: e100


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++dmesg++++++++++++++++++++++++++++++++++++++++++++++++++++
[    0.000000]   #5 [00008e1000 - 00008e41f0]              BRK ==> [00008e1000 - 00008e41f0]
[    0.004216] Initializing cgroup subsys net_cls
[    0.242402] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    0.242781] audit: initializing netlink socket (disabled)
[    0.927889] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    0.927892] e100: Copyright(c) 1999-2006 Intel Corporation
[    0.927946] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.956905] e100 0000:03:08.0: PME# disabled
[    0.963627] e100: eth0: e100_probe: addr 0xffaff000, irq 20, MAC addr 00:15:b7:0c:28:57
[    7.645200] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   99.701148] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   99.704172] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   99.708398] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  110.556033] eth0: no IPv6 routers present

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lsmod++++++++++++++++++++++++++++++++++++++++++++++++++++
e100                   28211  0 
mii                     4381  1 e100

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++END+++++++++++++++++++++++++++++++++++++++++++++++++++





i noticed it said my wlan was off, thats because i have to use rj45 to connect. i dont bother turning it on because i cant get anything wireless right now

---

### Post by eddski on 2011-08-28
heres the same output with the wlan on:


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++Sysyem-Info+++++++++++++++++++++++++++++++++++++++++++++++
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux eddski-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++ifconfig+++++++++++++++++++++++++++++++++++++++++++++++++
eth0      Link encap:Ethernet  HWaddr 00:15:b7:0c:28:57  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:b7ff:fe0c:2857/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2208906 (2.2 MB)  TX bytes:266856 (266.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3750 (3.7 KB)  TX bytes:3750 (3.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:53:62:b0  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe53:62b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3506 (3.5 KB)  TX bytes:4414 (4.4 KB)


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++iwconfig+++++++++++++++++++++++++++++++++++++++++++++++++
wlan0     IEEE 802.11abg  ESSID:"blonkerio"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:31:DE:B6   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++/pro/net/wireless+++++++++++++++++++++++++++++++++++++++++++++
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   70.  -33.  -256        0      0      0      0      0        0

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++/var/lib/NetworkManager/NetworkManager.state+++++++++++++++++++++++++++++++++

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lswh+++++++++++++++++++++++++++++++++++++++++++++++++++++
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:53:62:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.14 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:26 memory:ffcff000-ffcfffff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:15:b7:0c:28:57
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.13 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:ffaff000-ffafffff ioport:bf40(size=64)

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lspci++++++++++++++++++++++++++++++++++++++++++++++++++++
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at ffaff000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at bf40 [size=64]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Kernel driver in use: e100
	Kernel modules: e100


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++dmesg++++++++++++++++++++++++++++++++++++++++++++++++++++
[    0.000000]   #5 [00008e1000 - 00008e41f0]              BRK ==> [00008e1000 - 00008e41f0]
[    0.004217] Initializing cgroup subsys net_cls
[    0.242423] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    0.242806] audit: initializing netlink socket (disabled)
[    0.980535] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    0.980538] e100: Copyright(c) 1999-2006 Intel Corporation
[    0.980586] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.008096] e100 0000:03:08.0: PME# disabled
[    1.008780] e100: eth0: e100_probe: addr 0xffaff000, irq 20, MAC addr 00:15:b7:0c:28:57
[    6.898838] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   19.830710] Registered led device: iwl-phy0::radio
[   19.842551] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.870080] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.873160] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   19.873316] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.357082] wlan0: deauthenticating from 00:0f:66:31:de:b6 by local choice (reason=3)
[   30.358478] wlan0: direct probe to AP 00:0f:66:31:de:b6 (try 1)
[   30.360649] wlan0: direct probe responded
[   30.360656] wlan0: authenticate with AP 00:0f:66:31:de:b6 (try 1)
[   30.362616] wlan0: authenticated
[   30.362661] wlan0: associate with AP 00:0f:66:31:de:b6 (try 1)
[   30.365594] wlan0: RX AssocResp from 00:0f:66:31:de:b6 (capab=0x411 status=0 aid=2)
[   30.365599] wlan0: associated
[   30.368595] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.405043] eth0: no IPv6 routers present
[   40.872055] wlan0: no IPv6 routers present

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++++++++++++++++++++++++++++++++++++++++lsmod++++++++++++++++++++++++++++++++++++++++++++++++++++
e100                   28211  0 
mii                     4381  1 e100

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++END+++++++++++++++++++++++++++++++++++++++++++++++++++

---

### Post by eddski on 2011-08-31
sorry to have a double post as this was solved through my "Absolute beginners" post. Can someone tell me if it possible, and how to link to that post?
thanks

---

### Post by nm_geo on 2011-08-31
> **eddski said:**
> sorry to have a double post as this was solved through my "Absolute beginners" post. Can someone tell me if it possible, and how to link to that post?
thanks

[http://ubuntuforums.org/showthread.php?t=1809676](http://ubuntuforums.org/showthread.php?t=1809676)

There you go..

---


---
title: "No wifi networks on Thinkpad R40 w/ Cisco AIRONET Wireless Communications Device 5000"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by doc.aronnax on 2009-12-30
I just installed Ubuntu 9.10 on an IBM Thinkpad R40.  Although Ubuntu appears to be recognizing the wifi adapter, there are no visible wireless networks in the Network Manager.

The machine is an IBM Thinkpad R40, type 2681.

Running lspci -v tells me the following about the wireless card:

```

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
	Subsystem: AIRONET Wireless Communications Device 5000
	Flags: bus master, fast Back2Back, fast devsel, latency 64, IRQ 11
	I/O ports at 8000 [size=256]
	Memory at d0200000 (32-bit, non-prefetchable) [size=16K]
	Memory at d0400000 (32-bit, non-prefetchable) [size=4M]
	[virtual] Expansion ROM at f4000000 [disabled] [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: airo
	Kernel modules: airo

```

ifconfig tells me:

```

eth0      Link encap:Ethernet  HWaddr 00:06:1b:e1:44:37  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:1bff:fee1:4437/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11369820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2955418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3434779352 (3.4 GB)  TX bytes:227875346 (227.8 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:8a:5c:7e:03  
          inet6 addr: fe80::202:8aff:fe5c:7e03/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:4 dropped:0 overruns:0 frame:4
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:280 (280.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-02-8A-5C-7E-03-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:0 errors:4 dropped:0 overruns:0 frame:4
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:280 (280.0 B)
          Interrupt:11 Base address:0x8000 

```

iwconfig tells me:

```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-103 dBm
          Rx invalid nwid:19  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-103 dBm
          Rx invalid nwid:19  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40   Missed beacon:0

```

iwlist scan says:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

wifi0     No scan results

```

Help!

---


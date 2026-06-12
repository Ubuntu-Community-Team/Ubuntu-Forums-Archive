---
title: "wireless detected but not used?"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by vangop on 2010-08-06
Hi,
I have restored system backup from the other PC and everything seemed to be working fine. I just noticed that network manager is not managing the wifi.
It has 'enable networking', 'enable notifications' but no 'enable wireless'.
My wifi led is off, but the system detects killswitch.
```
Aug  6 10:50:07 zoidberg NetworkManager: <info>  WiFi now disabled by radio killswitch
Aug  6 10:50:11 zoidberg NetworkManager: <info>  WiFi now enabled by radio killswitch
```
```
$sudo lspci -v
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Dell Device 000b
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 16-00-75-ff-ff-44-e8-6f
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb

```
It says ```
Kernel driver in use: b43-pci-bridge
	Kernel modules: wl, ssb
```
and ssb is loaded ```
$ lsmod |grep ssb
ssb                    38671  1 b44

```
no eth1/wlan0 ifaces (used to have eth1 on the pc I made backup from).
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:03:b6:52:57  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:febf:5257/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6269813 (6.2 MB)  TX bytes:845620 (845.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12704 (12.7 KB)  TX bytes:12704 (12.7 KB)

```
Hardware drivers show that broadcomm drivers are in use. (proprietary sta)
Suggestions are welcome :)

---

### Post by dineshs on 2010-08-06
This may help
[http://beginlinux.com/twitter/1096-ubuntu-wireless-setup](http://beginlinux.com/twitter/1096-ubuntu-wireless-setup)

---

### Post by vangop on 2010-08-08
I just reinstalled the driver by unselecting/selecting.
Thanks anyway!

---


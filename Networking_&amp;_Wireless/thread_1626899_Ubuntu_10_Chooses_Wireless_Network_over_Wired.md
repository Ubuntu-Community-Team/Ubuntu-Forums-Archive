---
title: "Ubuntu 10 Chooses Wireless Network over Wired"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by ScottCh on 2010-11-20
Hi all,

I originally configured my desktop lucid lynx system to boot on our wireless network.  Later I added a 100 Mbps powerline/100baseT adapter set.  The system still boots to the wireless network and ignores the wired network.  The networkmanager applet's menu says that the wired network is unmanaged.

I can make the system use the wired network by turning off the wireless network in the networkmanager menu checkbox.  Unfortunately this erases the nameserver entries in /etc/resolv.conf, so I have to copy a backup resolv.conf file into place in order to have a nameserver.  After that the wired network works fine, but the  networkmanager applet still shows "no valid connections".

I have tried using Preferences->Network Connections to create a wired network connection.  However, it doesn't do anything, and it's gone the next time I reboot.

Having to go through this multi-step process to use wired networking after every bootup is a chore.  

After this manual process, "ifconfig eth2" shows:

eth2      Link encap:Ethernet  HWaddr 00:1d:7d:d3:18:64  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fed3:1864/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148885823 (148.8 MB)  TX bytes:4884017 (4.8 MB)
          Interrupt:26 Base address:0x2000 

Network devices:

00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
	Memory at ee102000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e400 [size=8]
	Memory at ee103000 (32-bit, non-prefetchable) [size=256]
	Memory at ee104000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

02:00.0 Network controller: RaLink RT2860
	Subsystem: ASUSTeK Computer Inc. Device 130f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ee000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta


Thanks for any pointers!

Scott C.
Cary, NC USA

---


---
title: "Advice on troubleshooting the Internet Connectivity (Netgear wireless adapter)"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by kamlesh30rao on 2009-02-04
Hi,

I need some help in troubleshooting my Internet Connection from the Ubuntu operating system.  Below is my config:

PC1 - Wired - DSL + Linksys Wireless Router (Windows OS - all working fine)

PC2 - Wireless(Netgear USB Adaper) - Multiboot - Windows/Ubuntu

Windows on PC2 is working fine with wireless internet.  When I boot the PC2 using Ubuntu OS, it is able to detect and connect to my Linksys wireless router.  It is even able to get the IP address, but not able to connect to the internet.  I am not able to browse any sites.  The Package Updaters are also failing.  

Please advice on fixing the problem.

Regards,
Kamlesh

---

### Post by ozbuntu01 on 2009-02-04
Hi kamlesh ,

I am also having very similar troubles as you. (Im a newbie)

Although I have Netgear DG834G router and a WPN111 USB Wireless Adapter.

Like you I am able to setup everything to what seems to be fine & connected to the internet. Although after few minutes , even seconds , the whole connection seems to get "Lost". (Cannot browse web , DL/UL speeds hang on 0kbps etc...

You can read my thread here [http://ubuntuforums.org/showthread.php?t=1059251](http://ubuntuforums.org/showthread.php?t=1059251) , with a in depth step by step guide of my setup. (Maybe it can shed some light on some aspect of your situation.

NOTE: What model is your Router/USB Adapter/Ubuntu ? (So others can get more info)

Also try checking out some of the output from network terminal commands


Cheers

---

### Post by kamlesh30rao on 2009-02-04
Hi ozbuntu01,

Thanks for providing me your thread.

Yes you are right.  I was also able to connect to Internet after a fresh installation of Ubuntu 8.10.  After few minutes, I lost the connection (similar case as yours)  

My Router is : Cisco LinkSys WRT54G
My USB : Netgear WG111v3
OS - Uubutu version 8.10 (32bit running on AMD desktop PC)

The same AMD Desktop PC is running Windows XP with Multiboot and everything is working fine from Win XP.

I will try to fetch output of ifconfig and post here for others to assist.

Hope we both find the solution soon!

Thanks,
Kamlesh

---

### Post by ozbuntu01 on 2009-02-04
:D

Unfortunately for you , It does NOT look like your NETGEAR WG111v3 is supported out of the box , as you can see in this wiki compatible wireless adapters list under "Netgear". [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)

Although there is a link provided with a guide for a successful manual installtion. Maybe it ccan apply to your situation. [http://ubuntuforums.org/showthread.php?p=5553916](http://ubuntuforums.org/showthread.php?p=5553916)


Welcome to the horrible world of Newer Netgear USB Wireless Adapters. lol

---

### Post by kamlesh30rao on 2009-02-04
Yes, you are right with the earlier version of Ubuntu, my Netgear WG111v3 didn't work and I had to do some manual steps.

But after a fresh install of Ubuntu 8.10, it has detected my wireless adapter and is also able to search the Wireless Connections.  It even shows the signal strength too.

Do you think that it has used some default drivers and hence not working fine?  I can give a try by installing the drivers again!

---

### Post by ozbuntu01 on 2009-02-04
Interesting.

I have the exact same problem with my Netgear WPN111 USB. It connects to internet & stays connected even after dropping out , as network manager says is still connected with full signal strength.

Try searching in your Linksys router settings and see if your router has any "View Attatched Devices" option in your router. This page should take a while to load up as it scans what devices are connected to the router and then provides you with what devices are connected.

In my Netgear DG834G Router , While the WPN111 still said it was "Connected" with "Full Signal Strength". I checked my router to be sure , and never the less the WPN111 USB Device was NOT in the list and was NOT being recognized.

Its really weird to hear you are having the same problem , even though your wireless adapter is SUPPORTED out of the box.
Although I am using Netgear WPN111 USB which is NOT supported out of the box yet, but I am having basically identical problems as you it seems.


Weird huh

---

### Post by ozbuntu01 on 2009-02-04
Bump ):P

---

### Post by cottfcfan on 2009-02-05
I am having exactly the same problem. wg111v3 installs and connects, shows signal strength, but no internet access.
 Is there a solution to this problem?

---

### Post by kamlesh30rao on 2009-02-05
From the PC1 (wired connection), when I see the Router Web Page, I can see the PC2 (Wireless connection) with the HOSTNAME shown in the Wireless Connections options.

Its really a wierd problem!  I'm yet to get the fix for this?

ozbuntu01 - Any new findings from your end?  By the way your name sounds to be some kind of advanced Ubuntu flavour!!! :) LOL

cottfcfan - welcome to the gang!  You have any updates on your problem. Any luck in fixing the issue?

---

### Post by kamlesh30rao on 2009-02-05
By the way, check this command```
ifconfig -a
```

Output is:

```

eth0      Link encap:Ethernet  HWaddr 00:14:85:7b:dd:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13560 (13.5 KB)  TX bytes:13560 (13.5 KB)

pan0      Link encap:Ethernet  HWaddr e2:47:ec:52:8b:aa  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:3a:37:ad  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fe3a:37ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1016 (1.0 KB)  TX bytes:12448 (12.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-2A-3A-37-AD-37-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Btw, how can I find out the Gateway being used?

---

### Post by ozbuntu01 on 2009-02-05
Hi cottfcfan ,

Welcome to the Buggy Netgear USB Wireless Adapter Club. lol.

There is NO solution that I know of yet for the - Netgear WG111v3 & WPN111 USB Wireless Adapters, hopefully there is a solution.

I am writing up a potential "Bug Report" to send to Launchpad as I think this maybe a potential bug. (As the Netgear WG111v3 is meant to be SUPPORTED out of the box)

..........................................................................................


@ kamlesh ,

Post up a few more network analysis outputs. I am creating a potential "Bug Report" & I will be referring this link/thread + also my link/thread to help assist with detailed information.

Start with posting up the output of these 2 commands.

```
 lspci -vvnn 
```

&

```
 dmesg 
```

.........................................................................................

@ Kamlesh ,

Your Gateway should be just your router ip address. Try looking on the bottom/sides of the router , they usually have the ip address somewhere on it.

To be sure you can visit the port forwarding guide here: [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

Choose your router model from the list , & then choose any program port forward guide as it does not matter , all we want is your router model ip address which should be mentioned in the port forwarding guides.

........................................................................................

>  Kamlesh - How do I find out the gateway being used ? 

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:3a:37:ad  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fe3a:37ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1016 (1.0 KB)  TX bytes:12448 (12.4 KB)



This should be your network card/computer ip address - inet addr:192.168.1.101

Your gateway ip should be something similar to this: 

192.168.1.1
or
192.168.1.254

Check the port forward guide to be sure.

---

### Post by kamlesh30rao on 2009-02-05
Yahoo! Big News!  Its working for me now.  Here is what I did (not sure if this fixed the problem).

- Connected my PC2 to Wired Internet
- Ran the Update Manager, which downloaded almost 230MB of updates.  It took more than 2 hours on my 256kbps broadband connection.
- Using the wired internet, also ran Add Remove programs and installed ndiswrapper Windows Wireless Driver program (from Add/Remove menu).  Although I am not using this, but still installed it.

- Switched off  my PC.  Removed wired internet and plugged in the NetGear USB Adapter and rebooted PC.
- Everything is up and running!

I didn't do any manual editing of any configuration files and got it working!  

@ ozbuntu1:

I will share the output of 2 commands soon.   

Regards,
Kamlesh

---

### Post by kamlesh30rao on 2009-02-05
Command:
```
lspci -vvnn
```
Output:
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f5] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-

00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f2000000-f5ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:0264]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c80 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:0264]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2) (prog-if 10)
	Subsystem: Giga-byte Technology Device [1458:5004]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f8005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2) (prog-if 20)
	Subsystem: Giga-byte Technology Device [1458:5004]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at f8006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device [f458:b000]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device [1458:b002]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at d400 [size=16]
	Region 5: Memory at f8004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device [1458:b002]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 23
	Region 0: I/O ports at 09e0 [size=8]
	Region 1: I/O ports at 0be0 [size=4]
	Region 2: I/O ports at 0960 [size=8]
	Region 3: I/O ports at 0b60 [size=4]
	Region 4: I/O ports at c000 [size=16]
	Region 5: Memory at f8008000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: c4000000-c40fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:a102]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)
	Subsystem: Giga-byte Technology Device [1458:e000]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f8007000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at e000 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: isp1760, forcedeth

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8129 [10ec:8129] (rev 10)
	Subsystem: Compex Device [11f6:8129]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 9000 [size=256]
	Region 1: Memory at f7000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at c4000000 [disabled] [size=64K]
	Kernel modules: r8169, 8139too

01:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
	Subsystem: Compro Technology, Inc. Device [185b:c200]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 32 (63750ns min, 63750ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f7101000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

01:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev 80) (prog-if 10)
	Subsystem: Giga-byte Technology Device [1458:1000]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at f7102000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at 9400 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400 GS [10de:0422] (rev a1)
	Subsystem: LeadTek Research Inc. Device [107d:20c8]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at a000 [size=128]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb


```

Command:
```
dmesg
```
Output:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000bfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff3000 - 00000000c0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xbfff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781e000 - 37fef6a1
[    0.000000] ACPI: RSDP 000F6BA0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT BFFF3000, 0030 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP BFFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT BFFF30C0, 4D95 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS BFFF0000, 0040
[    0.000000] ACPI: MCFG BFFF7F00, 003C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: APIC BFFF7E80, 0072 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] 2175MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781e000 - 0037fef6a1]          RAMDISK ==> [003781e000 - 0037fef6a1]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f51f0] 000f51f0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bfff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfff0
[    0.000000] On node 0 totalpages: 786319
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 552144 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779407
[    0.000000] Kernel command line: root=UUID=8bfb65ca-cdc3-4296-95ef-f02433878c10 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1808.188 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3102864k/3145664k available (2576k kernel code, 41516k reserved, 1165k data, 424k init, 2228160k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3616.37 BogoMIPS (lpj=7232752)
[    0.004032] Security Framework initialized
[    0.004039] SELinux:  Disabled at boot.
[    0.004066] AppArmor: AppArmor initialized
[    0.004075] Mount-cache hash table entries: 512
[    0.004249] Initializing cgroup subsys ns
[    0.004253] Initializing cgroup subsys cpuacct
[    0.004256] Initializing cgroup subsys memory
[    0.004272] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004275] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004287] Checking 'hlt' instruction... OK.
[    0.020399] SMP alternatives: switching to UP code
[    0.025804] ACPI: Core revision 20080609
[    0.027436] ACPI: Checking initramfs for custom DSDT
[    0.400311] ENABLING IO-APIC IRQs
[    0.400508] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.441036] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[    0.444027] Brought up 1 CPUs
[    0.444027] Total of 1 processors activated (3616.37 BogoMIPS).
[    0.444027] CPU0 attaching NULL sched-domain.
[    0.444027] net_namespace: 840 bytes
[    0.444027] Booting paravirtualized kernel on bare hardware
[    0.444027] Time:  8:17:30  Date: 02/06/09
[    0.444027] NET: Registered protocol family 16
[    0.444027] EISA bus registered
[    0.444027] ACPI: bus type pci registered
[    0.444027] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 31
[    0.444027] PCI: MCFG area at f0000000 reserved in E820
[    0.444027] PCI: Using MMCONFIG for extended config space
[    0.444027] PCI: Using configuration type 1 for base access
[    0.444027] ACPI: EC: Look up EC in DSDT
[    0.448208] ACPI Warning (dsobject-0501): Package List length (6) larger than NumElements count (2), truncated
[    0.448214]  [20080609]
[    0.452547] ACPI: Interpreter enabled
[    0.452551] ACPI: (supports S0 S1 S4 S5)
[    0.452566] ACPI: Using IOAPIC for interrupt routing
[    0.465810] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.466091] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.466095] pci 0000:00:03.0: PME# disabled
[    0.466122] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.466125] pci 0000:00:04.0: PME# disabled
[    0.466296] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.466340] PCI: 0000:00:0a.1 reg 20 io port: [1c00, 1c3f]
[    0.466346] PCI: 0000:00:0a.1 reg 24 io port: [1c80, 1cbf]
[    0.466366] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.466372] pci 0000:00:0a.1: PME# disabled
[    0.466432] PCI: 0000:00:0b.0 reg 10 32bit mmio: [f8005000, f8005fff]
[    0.466460] pci 0000:00:0b.0: supports D1
[    0.466462] pci 0000:00:0b.0: supports D2
[    0.466464] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.466469] pci 0000:00:0b.0: PME# disabled
[    0.466494] PCI: 0000:00:0b.1 reg 10 32bit mmio: [f8006000, f80060ff]
[    0.466524] pci 0000:00:0b.1: supports D1
[    0.466526] pci 0000:00:0b.1: supports D2
[    0.466528] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.466532] pci 0000:00:0b.1: PME# disabled
[    0.466567] PCI: 0000:00:0d.0 reg 20 io port: [f000, f00f]
[    0.466607] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.466612] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.466617] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.466622] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.466627] PCI: 0000:00:0e.0 reg 20 io port: [d400, d40f]
[    0.466633] PCI: 0000:00:0e.0 reg 24 32bit mmio: [f8004000, f8004fff]
[    0.466673] PCI: 0000:00:0f.0 reg 10 io port: [9e0, 9e7]
[    0.466678] PCI: 0000:00:0f.0 reg 14 io port: [be0, be3]
[    0.466683] PCI: 0000:00:0f.0 reg 18 io port: [960, 967]
[    0.466688] PCI: 0000:00:0f.0 reg 1c io port: [b60, b63]
[    0.466693] PCI: 0000:00:0f.0 reg 20 io port: [c000, c00f]
[    0.466699] PCI: 0000:00:0f.0 reg 24 32bit mmio: [f8008000, f8008fff]
[    0.466772] PCI: 0000:00:10.1 reg 10 32bit mmio: [f8000000, f8003fff]
[    0.466803] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.466807] pci 0000:00:10.1: PME# disabled
[    0.466834] PCI: 0000:00:14.0 reg 10 32bit mmio: [f8007000, f8007fff]
[    0.466840] PCI: 0000:00:14.0 reg 14 io port: [e000, e007]
[    0.466863] pci 0000:00:14.0: supports D1
[    0.466865] pci 0000:00:14.0: supports D2
[    0.466867] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.466871] pci 0000:00:14.0: PME# disabled
[    0.466976] PCI: bridge 0000:00:03.0 io port: [8000, 8fff]
[    0.467003] PCI: 0000:02:00.0 reg 10 32bit mmio: [f4000000, f4ffffff]
[    0.467011] PCI: 0000:02:00.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.467019] PCI: 0000:02:00.0 reg 1c 64bit mmio: [f2000000, f3ffffff]
[    0.467025] PCI: 0000:02:00.0 reg 24 io port: [a000, a07f]
[    0.467030] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.467078] PCI: bridge 0000:00:04.0 io port: [a000, afff]
[    0.467081] PCI: bridge 0000:00:04.0 32bit mmio: [f2000000, f5ffffff]
[    0.467085] PCI: bridge 0000:00:04.0 64bit mmio pref: [e0000000, efffffff]
[    0.467111] PCI: 0000:01:06.0 reg 10 io port: [9000, 90ff]
[    0.467118] PCI: 0000:01:06.0 reg 14 32bit mmio: [f7000000, f70000ff]
[    0.467140] PCI: 0000:01:06.0 reg 30 32bit mmio: [0, ffff]
[    0.467170] PCI: 0000:01:07.0 reg 10 32bit mmio: [f7101000, f71013ff]
[    0.467206] pci 0000:01:07.0: supports D1
[    0.467208] pci 0000:01:07.0: supports D2
[    0.467239] PCI: 0000:01:0e.0 reg 10 32bit mmio: [f7102000, f71027ff]
[    0.467246] PCI: 0000:01:0e.0 reg 14 io port: [9400, 947f]
[    0.467280] pci 0000:01:0e.0: supports D2
[    0.467282] pci 0000:01:0e.0: PME# supported from D2 D3hot D3cold
[    0.467286] pci 0000:01:0e.0: PME# disabled
[    0.467307] pci 0000:00:10.0: transparent bridge
[    0.467310] PCI: bridge 0000:00:10.0 io port: [9000, 9fff]
[    0.467314] PCI: bridge 0000:00:10.0 32bit mmio: [f6000000, f7ffffff]
[    0.467325] bus 00 -> node 0
[    0.467333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.467804] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.595330] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.595569] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[    0.595808] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.596053] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.596293] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[    0.596530] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.596768] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.597008] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.597248] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.597485] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.597725] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.597964] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.598204] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.598446] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.598685] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.598925] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.599164] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.599401] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.599642] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.599884] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.600187] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.600476] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.600763] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.601051] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.601344] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.601632] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.601920] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.602217] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.602507] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.602804] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.603095] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.603384] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.603675] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.603964] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.604257] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.604548] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.604837] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.605127] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.605417] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.605708] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.605997] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.606194] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.606228] pnp: PnP ACPI init
[    0.606236] ACPI: bus type pnp registered
[    0.613431] pnp: PnP ACPI: found 13 devices
[    0.613434] ACPI: ACPI bus type pnp unregistered
[    0.613438] PnPBIOS: Disabled by ACPI PNP
[    0.613781] PCI: Using ACPI for IRQ routing
[    0.613916] NET: Registered protocol family 8
[    0.613916] NET: Registered protocol family 20
[    0.613916] NetLabel: Initializing
[    0.613916] NetLabel:  domain hash size = 128
[    0.613916] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.613916] NetLabel:  unlabeled traffic allowed by default
[    0.613916] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.613916]    actual entries 65620
[    0.613916] AppArmor: AppArmor Filesystem Enabled
[    0.613916] ACPI: RTC can wake from S4
[    0.613916] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.613916] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.613916] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.613916] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.613916] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.613916] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.613916] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.613916] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.613916] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.613916] system 00:01: iomem range 0xf0000000-0xf1ffffff could not be reserved
[    0.613916] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.613916] system 00:02: ioport range 0x290-0x29f has been reserved
[    0.613916] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.613916] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.613916] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.613916] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.613916] system 00:0c: iomem range 0xbfff0000-0xbfffffff could not be reserved
[    0.613916] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.613916] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.613916] system 00:0c: iomem range 0x100000-0xbffeffff could not be reserved
[    0.613916] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.613916] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.650002] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.650005] pci 0000:00:03.0:   IO window: 0x8000-0x8fff
[    0.650009] pci 0000:00:03.0:   MEM window: disabled
[    0.650012] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.650018] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.650021] pci 0000:00:04.0:   IO window: 0xa000-0xafff
[    0.650024] pci 0000:00:04.0:   MEM window: 0xf2000000-0xf5ffffff
[    0.650028] pci 0000:00:04.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.650033] pci 0000:00:10.0: PCI bridge, secondary bus 0000:01
[    0.650037] pci 0000:00:10.0:   IO window: 0x9000-0x9fff
[    0.650041] pci 0000:00:10.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.650045] pci 0000:00:10.0:   PREFETCH window: 0x000000c4000000-0x000000c40fffff
[    0.650057] pci 0000:00:03.0: setting latency timer to 64
[    0.650063] pci 0000:00:04.0: setting latency timer to 64
[    0.650069] pci 0000:00:10.0: setting latency timer to 64
[    0.650072] bus: 00 index 0 io port: [0, ffff]
[    0.650075] bus: 00 index 1 mmio: [0, ffffffff]
[    0.650078] bus: 03 index 0 io port: [8000, 8fff]
[    0.650080] bus: 03 index 1 mmio: [0, 0]
[    0.650082] bus: 03 index 2 mmio: [0, 0]
[    0.650084] bus: 03 index 3 mmio: [0, 0]
[    0.650086] bus: 02 index 0 io port: [a000, afff]
[    0.650089] bus: 02 index 1 mmio: [f2000000, f5ffffff]
[    0.650091] bus: 02 index 2 mmio: [e0000000, efffffff]
[    0.650094] bus: 02 index 3 mmio: [0, 0]
[    0.650096] bus: 01 index 0 io port: [9000, 9fff]
[    0.650098] bus: 01 index 1 mmio: [f6000000, f7ffffff]
[    0.650101] bus: 01 index 2 mmio: [c4000000, c40fffff]
[    0.650103] bus: 01 index 3 io port: [0, ffff]
[    0.650106] bus: 01 index 4 mmio: [0, ffffffff]
[    0.650118] NET: Registered protocol family 2
[    0.650150] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.650150] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.650150] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.650150] TCP: Hash tables configured (established 131072 bind 65536)
[    0.650150] TCP reno registered
[    0.650150] NET: Registered protocol family 1
[    0.650150] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.020725]  it is
[    1.419420] Freeing initrd memory: 8005k freed
[    1.420173] audit: initializing netlink socket (disabled)
[    1.420190] type=2000 audit(1233908250.420:1): initialized
[    1.426820] highmem bounce pool size: 64 pages
[    1.426826] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.429087] VFS: Disk quotas dquot_6.5.1
[    1.429178] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.429277] msgmni has been set to 1725
[    1.429401] io scheduler noop registered
[    1.429404] io scheduler anticipatory registered
[    1.429406] io scheduler deadline registered
[    1.429418] io scheduler cfq registered (default)
[    1.429438] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.429478] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.429489] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.429514] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.444056] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.444069] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.444080] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.444094] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.444118] pci 0000:02:00.0: Boot video device
[    1.444238] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.444267] pcieport-driver 0000:00:03.0: found MSI capability
[    1.444291] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.444333] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.444407] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.444435] pcieport-driver 0000:00:04.0: found MSI capability
[    1.444455] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.444492] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.444776] isapnp: Scanning for PnP cards...
[    1.797751] isapnp: No Plug & Play device found
[    1.834440] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.834578] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.835269] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.837041] brd: module loaded
[    1.837115] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.837236] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.840085] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.840091] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.840503] mice: PS/2 mouse device common for all mice
[    1.840637] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.840665] rtc0: alarms up to one year, y3k
[    1.840788] EISA: Probing bus 0 at eisa.0
[    1.840795] Cannot allocate resource for EISA slot 1
[    1.840798] Cannot allocate resource for EISA slot 2
[    1.840815] Cannot allocate resource for EISA slot 8
[    1.840817] EISA: Detected 0 cards.
[    1.840821] cpuidle: using governor ladder
[    1.840823] cpuidle: using governor menu
[    1.841366] TCP cubic registered
[    1.841395] Using IPI No-Shortcut mode
[    1.841592] registered taskstats version 1
[    1.841745]   Magic number: 13:988:269
[    1.841793] tty ttyue: hash matches
[    1.841944] rtc_cmos 00:04: setting system clock to 2009-02-06 08:17:32 UTC (1233908252)
[    1.841948] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.841950] EDD information not available.
[    1.842228] Freeing unused kernel memory: 424k freed
[    1.842293] Write protecting the kernel text: 2580k
[    1.842332] Write protecting the kernel read-only data: 940k
[    1.870546] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.076062] fuse init (API version 7.9)
[    2.352619] processor ACPI0007:00: registered as cooling_device0
[    3.693896] usbcore: registered new interface driver usbfs
[    3.693925] usbcore: registered new interface driver hub
[    3.707025] No dock devices found.
[    3.735505] usbcore: registered new device driver usb
[    3.760985] SCSI subsystem initialized
[    3.761565] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[    3.761573] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
[    3.761584] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    3.761588] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.761635] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    3.761675] ehci_hcd 0000:00:0b.1: debug port 1
[    3.761680] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    3.761693] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xf8006000
[    3.773069] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.773232] usb usb1: configuration #1 chosen from 1 choice
[    3.773264] hub 1-0:1.0: USB hub found
[    3.773274] hub 1-0:1.0: 8 ports detected
[    3.815538] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.852062] libata version 3.00 loaded.
[    3.980906] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    3.980916] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
[    3.980930] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    3.980934] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.980959] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    3.980982] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xf8005000
[    4.038406] usb usb2: configuration #1 chosen from 1 choice
[    4.038435] hub 2-0:1.0: USB hub found
[    4.038447] hub 2-0:1.0: 8 ports detected
[    4.092072] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.140341] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.140821] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    4.140829] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    4.140834] forcedeth 0000:00:14.0: setting latency timer to 64
[    4.140860] nv_probe: set workaround bit for reversed mac addr
[    4.231622] usb 1-1: configuration #1 chosen from 1 choice
[    4.661014] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x3f1 @ 7, addr 00:14:85:7b:dd:f8
[    4.661019] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    4.661080] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.661556] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    4.661564] r8169 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    4.661571] r8169 0000:01:06.0: cache line size of 64 is not supported
[    4.661577] r8169 0000:01:06.0: PCI INT A disabled
[    4.661584] r8169: probe of 0000:01:06.0 failed with error -22
[    4.666378] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    4.666386] ohci1394 0000:01:0e.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    4.719102] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[f7102000-f71027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.725901] 8139too Fast Ethernet driver 0.9.28
[    4.737940] 8139too 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    4.737956] 8139too 0000:01:06.0: Chip not responding, ignoring board
[    4.737965] 8139too 0000:01:06.0: PCI INT A disabled
[    4.737972] 8139too: probe of 0000:01:06.0 failed with error -5
[    4.738293] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    4.738774] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    4.738781] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    4.738800] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    4.738808] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    4.738820] sata_nv 0000:00:0e.0: version 3.5
[    4.738825] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    4.738828] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    4.738853] sata_nv 0000:00:0e.0: setting latency timer to 64
[    4.739269] scsi0 : sata_nv
[    4.739366] scsi1 : sata_nv
[    4.739588] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 20
[    4.739592] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 20
[    5.204056] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.404191] ata1.00: HPA unlocked: 586070255 -> 586072368, native 586072368
[    5.404198] ata1.00: ATA-7: ST3300820AS, 3.AAC, max UDMA/133
[    5.404201] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.447163] ata1.00: configured for UDMA/133
[    5.756122] scsi 0:0:0:0: Direct-Access     ATA      ST3300820AS      3.AA PQ: 0 ANSI: 5
[    5.756703] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    5.756708] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    5.756745] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    5.756756] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    5.756774] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    5.756777] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    5.756807] sata_nv 0000:00:0f.0: setting latency timer to 64
[    5.757347] scsi2 : sata_nv
[    5.757617] scsi3 : sata_nv
[    5.757828] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 23
[    5.757832] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 23
[    6.008752] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00001485007a5cd2]
[    6.387048] pata_amd 0000:00:0d.0: version 0.3.10
[    6.387097] pata_amd 0000:00:0d.0: setting latency timer to 64
[    6.393348] scsi4 : pata_amd
[    6.396070] scsi5 : pata_amd
[    6.396913] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    6.396917] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    6.397773] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.417610] Driver 'sd' needs updating - please use bus_type methods
[    6.417712] sd 0:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
[    6.417729] sd 0:0:0:0: [sda] Write Protect is off
[    6.417732] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.417756] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.417822] sd 0:0:0:0: [sda] 586072368 512-byte hardware sectors (300069 MB)
[    6.417835] sd 0:0:0:0: [sda] Write Protect is off
[    6.417838] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.417860] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.417865]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    6.513993] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.560416] ata5.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
[    6.560436] ata5: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    6.576358] ata5.00: configured for UDMA/33
[    6.576391] ata6: port disabled. ignoring.
[    6.577790] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.05 PQ: 0 ANSI: 5
[    6.577961] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    6.617336] Driver 'sr' needs updating - please use bus_type methods
[    6.621413] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.621419] Uniform CD-ROM driver Revision: 3.20
[    6.621518] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.335575] PM: Starting manual resume from disk
[    7.335580] PM: Resume from partition 8:10
[    7.335582] PM: Checking hibernation image.
[    7.335766] PM: Resume from disk failed.
[    7.373282] kjournald starting.  Commit interval 5 seconds
[    7.373298] EXT3-fs: mounted filesystem with ordered data mode.
[   11.920642] udevd version 124 started
[   12.800258] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.812041] ACPI: Power Button (FF) [PWRF]
[   12.812162] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.824018] ACPI: Power Button (CM) [PWRB]
[   13.080162] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.128449] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.334978] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   13.335011] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   13.534995] parport_pc 00:09: reported by Plug and Play ACPI
[   13.535060] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.495082] Linux video capture interface: v2.00
[   16.729419] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   16.729425] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   16.729445] HDA Intel 0000:00:10.1: setting latency timer to 64
[   16.814936] saa7130/34: v4l2 driver version 0.2.14 loaded
[   16.815849] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   16.815859] saa7134 0000:01:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   16.815866] saa7134[0]: found at 0000:01:07.0, rev: 1, irq: 17, latency: 32, mmio: 0xf7101000
[   16.815873] saa7134[0]: subsystem: 185b:c200, board: Compro VideoMate Gold+ Pal [card=49,autodetected]
[   16.815884] saa7134[0]: board init: gpio is cc003f
[   16.815985] input: saa7134 IR (Compro VideoMate Go as /devices/pci0000:00/0000:00:10.0/0000:01:07.0/input/input4
[   16.865234] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   16.984739] saa7134[0]: i2c eeprom 00: 5b 18 00 c2 ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984749] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984757] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984766] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984774] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984782] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff 01 01 ff 01 ff 00 07 34 03 cb
[   16.984790] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984798] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984806] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984814] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984822] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984830] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984838] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984846] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984854] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.984862] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.033733] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[   17.033736]          hardware, use at your own risk
[   17.035755] phy0: Selected rate control algorithm 'pid'
[   17.226017] phy0: hwaddr 00:1e:2a:3a:37:ad, RTL8187BvE V0 + rtl8225z2
[   17.226039] usbcore: registered new interface driver rtl8187
[   17.244101] tuner' 2-0060: chip found @ 0xc0 (saa7134[0])
[   17.244176] tea5767 2-0060: type set to Philips TEA5767HN FM Radio
[   17.260044] tuner' 2-0063: chip found @ 0xc6 (saa7134[0])
[   17.268052] tuner' 2-0068: chip found @ 0xd0 (saa7134[0])
[   17.336063] tuner-simple 2-0063: creating new instance
[   17.336068] tuner-simple 2-0063: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   17.346915] saa7134[0]: registered device video0 [v4l2]
[   17.346975] saa7134[0]: registered device vbi0
[   17.347027] saa7134[0]: registered device radio0
[   17.448519] saa7134 ALSA driver for DMA sound loaded
[   17.448555] saa7134[0]/alsa: saa7134[0] at 0xf7101000 irq 17 registered as card -2
[   17.627510] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   19.939161] lp0: using parport0 (interrupt-driven).
[   20.061440] Adding 1453840k swap on /dev/sda10.  Priority:-1 extents:1 across:1453840k
[   20.621921] EXT3 FS on sda9, internal journal
[   21.524025] type=1505 audit(1233888471.716:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4207
[   21.753321] type=1505 audit(1233888471.948:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4212
[   21.753587] type=1505 audit(1233888471.948:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4212
[   21.864169] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.433705] ACPI: WMI: Mapper loaded
[   22.717692] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[   22.717726] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   22.717729] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   23.349106] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.403967] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   23.403973] apm: overridden by ACPI.
[   23.566058] ppdev: user-space parallel port driver
[   25.026153] Bluetooth: Core ver 2.13
[   25.027716] NET: Registered protocol family 31
[   25.027721] Bluetooth: HCI device and connection manager initialized
[   25.027725] Bluetooth: HCI socket layer initialized
[   25.042451] Bluetooth: L2CAP ver 2.11
[   25.042456] Bluetooth: L2CAP socket layer initialized
[   25.054585] Bluetooth: SCO (Voice Link) ver 0.6
[   25.054590] Bluetooth: SCO socket layer initialized
[   25.071605] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.071611] Bluetooth: BNEP filters: protocol multicast
[   25.100175] Bridge firewalling registered
[   25.110626] Bluetooth: RFCOMM socket layer initialized
[   25.111171] Bluetooth: RFCOMM TTY layer initialized
[   25.111176] Bluetooth: RFCOMM ver 1.10
[   26.742990] mtrr: base(0xe0000000) is not aligned on a size(0xff00000) boundary
[   27.148031] Clocksource tsc unstable (delta = -165322028 ns)
[   29.189399] eth0: no link during initialization.
[   39.350781] saa7134[0]/irq[10,-65163]: r=0x20 s=0x00 PE
[   39.350792] saa7134[0]/irq: looping -- clearing PE (parity error!) enable bit
[   45.352690] NET: Registered protocol family 17
[   48.313997] wlan0: authenticate with AP 00:1e:e5:69:84:e0
[   48.316251] wlan0: authenticated
[   48.316260] wlan0: associate with AP 00:1e:e5:69:84:e0
[   48.319526] wlan0: RX AssocResp from 00:1e:e5:69:84:e0 (capab=0x421 status=0 aid=1)
[   48.319536] wlan0: associated
[   48.320256] wlan0: disassociating by local choice (reason=3)
[   61.922002] wlan0: authenticate with AP 00:1e:e5:69:84:e0
[   61.924344] wlan0: authenticated
[   61.924354] wlan0: associate with AP 00:1e:e5:69:84:e0
[   61.926384] wlan0: RX ReassocResp from 00:1e:e5:69:84:e0 (capab=0x421 status=0 aid=1)
[   61.926392] wlan0: associated
[   72.630041] NET: Registered protocol family 10
[   72.632874] lo: Disabled Privacy Extensions
[   72.634798] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   83.396024] wlan0: no IPv6 routers present
[  128.136164] ppdev0: registered pardevice
[  128.184060] ppdev0: unregistered pardevice
[  129.028804] ppdev0: registered pardevice
[  129.076266] ppdev0: unregistered pardevice
[  129.147044] ppdev0: registered pardevice
[  129.196587] ppdev0: unregistered pardevice

```

---

### Post by kamlesh30rao on 2009-02-05
Command:
```
uname -a
```
Output:
```
Linux amd-ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
```

Command:
```
lsusb
```
Output:
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The command:
```
ndiswrapper -l
```
does not return any output.

Command:
```
iwconfig
```
Output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LSHomeRouter"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:E5:69:84:E0   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=72/100  Signal level:-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by ozbuntu01 on 2009-02-05
@ Kamlesh ,

Thats great news :D

Very glad to hear you got your Netgear WG111v3 USB Wireless Adapter working. Maybe the WG111v3 IS supported out of the box to sum degree. (After installing updates and watnot)

Keep us updated Kamlesh with the WG111v3 performance.

..............................................................................

@ cottfcfan ,

You should try the same procedure as Kamlesh for your WG111v3 and see what happens. Tell us what happens.

---

### Post by kamlesh30rao on 2009-02-06
So far so good.  Its running smoothly.  The performance is good so far.  I have installed some more additional packages online (c, c++ libraries etc)

In fact now I am looking for some help for Dual View setup.  My Ubuntu PC is connected to both ViewSonic LCD Monitor and LG LCD Television.

---

### Post by ozbuntu01 on 2009-02-06
@ Kamlesh ,

Good to hear things are still running smoothly with the Netgear WG111v3.

............................................................................

Try following this guide for dual monitor display.


1) The first step towards dual monitors involves installing the NVidia 3D drivers.

2) Open terminal and type ```
 sudo apt-get install nvidia-glx 
```

3) Now the Nvidia drivers are installed , you need to check that you are using them. Type ```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
```

This ensures that we have a backup copy in case some of the settings we’re about to edit break X and don’t allow you to use a graphical interface!

4) Now we are ready to edit settings. Type ```
 sudo gedit /etc/X11/xorg.conf 
```

5) Under the module section, replace “nv” with “glx”. Under the device heading, make sure that Driver says “nvidia”.

6) _Under the screen section, add the following line:_ Option “RenderAccel” “true”

7) Now save your changes and close gedit.

8) We’re going to reload X to ensure that we’re now using the proper drivers. Reload X by hitting Ctrl+Alt+Backspace. This will require you to log back into Ubuntu.

9) If our install worked, you should see the NVidia logo flash quickly before the Ubuntu log in screen comes up. Actually, if this doesn’t work, you’re not going to be able to load X properly. If that’s the case, you’re going to have to type this into the console to replace the new xorg.conf with the old. ```
 sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 
```

10) Assuming everything went well, we’re quite close to having dual screens working. Let’s go back into xorg.conf using ```
 sudo gedit /etc/X11/xorg.conf 
```. Now go back under the heading “Screen”. Let’s add a few lines:

##This turns on NVidia’s TwinView
Option “TwinView”
##Here I’m setting the resolution to the individual monitors.
Option “MetaModes” “1280×1024 1280×1024&#8243;

11) That should be it! Restart X with Ctrl+Alt+Backspace and you should have two screens. If the orientation of the screens is off, try this under the “Screen” heading…

Option “TwinViewOrientation” “LeftOf”

LeftOf can be LeftOf, RightOf, Below, Above, or Clone.



Hope that was helpful!

---

### Post by wfdudley on 2009-02-15
Hello,

I can't directly address your WPN111 problems, since my WPN111 seems
to work fine on my 8.04 (Hardy) installation, but I will suggest that
you might want to see if you have the proper routes set up once you
get a connection to your wireless router.

After you get your wireless connection, try this:

```
route -n
```

Here's the output on my box, using WPN111:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan3
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan3
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

My WPN111 is wlan3 (I have three other wireless interfaces I can use).
You can ignore the eth0 lines in the output of route -n, since eth0
isn't connected.

The first wlan3 row says that packets to the 192.168.1.0 LAN don't
need any special routing.

The second wlan3 row says that packets to the outside world (0.0.0.0)
should be routed through the gateway 192.168.1.254, which is the
address of my router.

If your routing table doesn't look like this than that may indicate
why you can't connect to the internet even though you have a wireless
connection to your router.

The router table should be set up correctly when the IP address is
assigned via dhcp, so I cannot explain **why** your routing table
might be wrong.

Good luck,
Bill

---


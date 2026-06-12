---
title: "Dell Brodcom Drivers"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by nikhilneela on 2011-02-27
Hi,
I have installed Wireless drivers in ubuntu 10.04. when i say ifconfig it shows both eth0 and eth1. But still i do not find wireless network icon in top right panel. I browsed through the forums and found that typing nm-applet will show the networks available but the command simply returns an instance is already avaialable. Any help??

---

### Post by amsterdamharu on 2011-02-27
I think the network icon looks like 2 monitors, you click on that and it should show available wireless networks. If it doesn't could you post the output of the following commands?

Is it a usb or pci wireless card, if it's usb please post the output of the following command:
```
sudo lsusb -vv
```
if it's pci please post the output of the following command:
```
sudo lspci -vv
```
[COLOR=Red]You need to post only the part of your wireless card.[/COLOR]
Can you post the output of the following command as well?
```
rfkill list
ifconfig -a
sudo jockey-text
```
If rfkill says it's not installed you can install it with the following command:
```
sudo apt-get install rfkill
```


To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by nikhilneela on 2011-02-27
Hi amsterdamharu,
  Here is the output of the commands which u asked. Everthing except the last, jockey-text didnot yeild any output. Just gave searching for available drivers...

output for lspci
```

12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Device 0010
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fbd00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [d0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
			ClockPM+ Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-00-a1-ff-ff-bf-70-f1
	Capabilities: [16c v1] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl

13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Dell Device 0447
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 45
	Region 0: I/O ports at d000 [size=256]
	Region 2: Memory at d0c10000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at d0c00000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fb300000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 4181
	Capabilities: [70] Express (v2) Endpoint, MSI 01
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
		Vector table: BAR=4 offset=00000000
		PBA: BAR=4 offset=00000800
	Capabilities: [cc] Vital Product Data
		Unknown small resource type 00, will not decode more.
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP+ BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 02-00-00-00-36-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

```

output for rfkill list
```

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

output for ifconfig -a
```

br0       Link encap:Ethernet  HWaddr a4:ba:db:d9:35:59  
          inet addr:192.168.110.85  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a6ba:dbff:fed9:3559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:19145 (19.1 KB)

eth0      Link encap:Ethernet  HWaddr a4:ba:db:d9:35:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 70:f1:a1:bf:de:2c  
          inet addr:192.168.110.85  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::72f1:a1ff:febf:de2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2670748 (2.6 MB)  TX bytes:2670748 (2.6 MB)

virbr0    Link encap:Ethernet  HWaddr 36:bf:10:4e:fa:5d  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::34bf:10ff:fe4e:fa5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:18862 (18.8 KB)

```

output for sudo jockey-start
```

nikhil@ubuntu:~/Desktop$ sudo jockey-text

Searching for available drivers...
nikhil@ubuntu:~/Desktop$ 

```

---

### Post by amsterdamharu on 2011-02-27
Thank you for posting the output, according to the output of ifconfig you are connected to the Internet. If you unplug the network cables from the computer and then open a browser are you able to go to google.com for example?

If not could you try ifconfig -a again and see if br0 has an IP address.

Then could you try to open [http://192.168.0.1]("http://92.168.0.1") in a browser? If you can then your wireless is working fine and connecting to your router but your router is not connecting to the Internet.

If the nmapplet does not show in your panel then could you give us the output of the following command.

```
cat /etc/networks
```

---

### Post by nikhilneela on 2011-02-27
Thanks for ur concern.I unplugged the network cable and then opened the browser, but it could not connect. I tried to ping my gateway 192.168.3.254, it said destination unreachable and also there is no file in /etc/networks/. The following is the output when i restart the networking /etc/init.d/networking restart
```

* Reconfiguring network interfaces...                                                                                                                                   * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
SIOCDELRT: No such process
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
 * Starting iSCSI initiator service iscsid
   ...done.
 * Setting up iSCSI targets
   ...done.
ssh stop/waiting
ssh start/running, process 9782

Waiting for br0 to get ready (MAXWAIT is 20 seconds).
 * Setting up iSCSI targets
   ...done.
ssh stop/waiting
ssh start/running, process 10346
 * Setting up iSCSI targets
   ...done.
ssh stop/waiting
ssh start/running, process 10732
                                                                                                                                                                 [ OK ]
root@ubuntu:/home/nikhil# 


```

The following is the output of the file /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
	address 192.168.110.85
	netmask 255.255.0.0
	network 192.168.0.0
	broadcast 192.168.255.255
	gateway 192.168.3.254
	nameserver 192.168.3.254 
auto br0
	iface br0 inet static
 	address 192.168.110.85
 	netmask 255.255.0.0
 	network 192.168.0.0
 	broadcast 192.168.255.255
 	gateway 192.168.3.254
 	dns-nameservers 192.168.3.254
 	dns-search google.com
 	bridge_ports eth0
 	bridge_fd 9
 	bridge_hello 2
 	bridge_maxage 12
 	bridge_stp off
auto eth1
iface eth1 inet static
	address 192.168.110.85
	netmask 255.255.0.0
	network 192.168.0.0
	broadcast 192.168.255.255
	gateway 192.168.3.254
	nameserver 192.168.3.254 


```

---

### Post by amsterdamharu on 2011-02-27
```
cat /etc/networks
```
Could you copy and paste that command and post the output of that?

> NetworkManager will only handle interfaces not declared in /etc/network/interfaces
from
[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)

In other words you should remove everything from that file except the 2 lines:
```
auto lo
iface lo inet loopback

```

To do that press alt + F2 type "gksu gedit" (no quotes) and click run. When removed all the lines but the 2 mentioned above save the file and execute the following commands:

```
sudo service network-manager stop
sudo service network-manager start
nm-applet
```

Now you can use the network manager applet to set up your networks, either give it static ip or let dhcp handle it (under ip4 tab).

---

### Post by kevdog on 2011-02-27
Hold on for a minute here.  You are using the broadcom 4313 chipset that is associated with the wl kernel module.  So what exactly is the problem?

---

### Post by nikhilneela on 2011-02-27
Thank you Amsterdam, That worked. I am able to see the applet and internet is working for me now. what mistake did i do? Editing /etc/networks/interfaces should not be done??

---

### Post by amsterdamharu on 2011-02-27
You didn't do anything wrong, there are tutorials that will have you use iwconfig or change the /etc/network/interfaces file. 
There is nothing wrong with that but it's a harder way of doing it. Network manager and the nm-applet will not touch any network interface if they are mentioned in that file, this is normal behavior because you edited those files because you don't want network-manager to handle the connections.

---

### Post by nikhilneela on 2011-02-28
But since i edited that file according to what i want.(I edited as per IP address and others), I must be able to access internet? why was i not able to access previously and why am i able to access now? What if we want to edit files, How can we access internet when we edit those files as per our IP?

---

### Post by amsterdamharu on 2011-02-28
I don't know what would be wrong with the file but there is probably something wrong with it. Using the file and typing your settings there is more errorprone than using nm-applet and letting network-manager connect for you.

Did you use iwconfig to fill that file or did you type it yourself? Probably using iwconfig would make it a little less complicated.

---


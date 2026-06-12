---
title: "No Wireless with Atheros 5007G"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by alligoodw on 2009-03-09
I've tried a couple of things to no avail.  I have ubuntu 8.4 installed on a HP Pavilion dv6000.  Please note the following stats:

**lsusb**
Bus 004 Device 003: ID 0408:030c Quanta Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  
[B]
lspci[/B]
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



**lshw -c network**
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)



**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1e:68:73:53:79  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe73:5379/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2194647 (2.0 MB)  TX bytes:488130 (476.6 KB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5800 (5.6 KB)  TX bytes:5800 (5.6 KB)


[B]
 iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.


[B]
iwlist wlano scan[/B]
wlano     Interface doesn't support scanning.


I am entirely at a loss.  I need to know what needs to be turned off and what needs to be turned on.  I need to know what to install and what not to install.  I need someone to walk me through and get this thing set up. I believe this to be the last piece of hardware to set up and get it running properly.

---

### Post by 67GTA on 2009-03-09
I would recommend using ndiswrapper for 8.04. I wrote a small how to here for 32bit: [http://forums.linuxmint.com/viewtopic.php?f=49&t=13980&hilit=+ndiswrapper](http://forums.linuxmint.com/viewtopic.php?f=49&t=13980&hilit=+ndiswrapper)

EDIT: You can install ndiswrapper with the install CD. Just add the CD as a repo with Synaptic or from the software sources app.

---

### Post by avtolle on 2009-03-09
Since you are using 8.04, and have an Atheros wireless card, see [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) and, while reading this, take a look at the comments in the thread.

---

### Post by alligoodw on 2009-03-10
67GTA,

I followed your instructions and I'm finally able to recognize the Atheros driver; it shows a connection of 100%.  However, I've not been able to connect regardless of what method I use - asii, hex, wpa personal etc; I have a password protected connection.  

I have a question.  Is it possible I'm using the wrong driver (Atheros 5007EG)?  What I actually have is an Atheros 5007, not EG, card in my system. Do I need to find a driver specific for 5007 and not 5007EG?  If so, where can I download it?

---

### Post by 67GTA on 2009-03-10
Post the output of ```
iwconfig
```

---

### Post by alligoodw on 2009-03-10
Here it is:

** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by 67GTA on 2009-03-11
You have the right driver. Have you tried connecting to an unencrypted connection? Is the connection encrypted, or just password protected? If it is encrypted (WPA), you will need to set up WPA. Good guide here: [http://ubuntuportal.blogspot.com/2007/02/how-to-enable-wpa-with-ndiswrapper.html](http://ubuntuportal.blogspot.com/2007/02/how-to-enable-wpa-with-ndiswrapper.html)

---


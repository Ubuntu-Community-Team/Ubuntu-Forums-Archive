---
title: "Disappointed Ubuntu Newbie - WPA2 + NIC Woes"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by AP0ll0UK on 2009-01-05
As the subject says I'm a disappointed Ubuntu newbie desperately trying to break away from the not so fluffy Microsoft world!

I'm running a Dell X300 which has an internal Intel 2100 Mini-PCI card and a Netgear WG511T.

Both cards appear to be installed ok, however, when trying to join my Wireless LAN [secured using WPA2 Personal] I am presented with the request for the key. Once entered, the laptop tries to join the Wireless LAN and then asks for the key again - round and round we go, unfortunately this is where I am stuck. I have tried this with both adapters and but present me with th e 

Can anyone help me with this please before my new Ubuntu installation gets overwritten with XP :D

---

### Post by AP0ll0UK on 2009-01-06
*Bump*

---

### Post by ELF_O8 on 2009-01-06
First of all, try to avoid bumping your thread more than once every 24 hours.
That said, what kind of encryption are you using on the key?
AES, TKIP?

---

### Post by AP0ll0UK on 2009-01-06
Apologies, I checked my post and saw how far down the list it had dropped in such a short space of time and not wanting to abandon this project I bumped it.

With regards to the key type, I'm using AES. 

I'm using a Linksys WRT300N and everything my wireless Windows devices can connect to the Wireless Lan with no problems. The shared key is made up of upper and lower case letters, numbers and alpha-numerics.

My laptop is the first device I would hope to use Ubuntu on and it would replace the XP SP3 installation. Once I've tested it for a few weeks and become more familar with the OS Pro's and Con's then I can make a much more informed decision as to whether Ubuntu goes on my server and HTPC.

The laptop is part of a much bigger project but without wireless access on my laptop, Ubuntu is usless to me. I appreciate that may sound very short sighted but my prerequisite to getting my own Ubuntu prokect off of the ground is trialing it on my laptop.

Thanks again.

---

### Post by ELF_O8 on 2009-01-06
Could you post the output of lspci and ifconfig when the card is plugged in?
```
lspci -v
```
```
ifconfig
```

---

### Post by Coombabah on 2009-01-06
> **AP0ll0UK said:**
> Can anyone help me with this please before my new Ubuntu installation gets overwritten with XP :D

It may be an issue with Intrepid.

Try booting Hardy off a live CD and see if you can easily get wireless working.

---

### Post by AP0ll0UK on 2009-01-07
Thanks for your replies. 

First the results from lspci -v [Please note that my laptop was connect into my LAN at the time this information was collected]

dave@cyclops:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Dell Device 014f
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Dell Device 014f
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Dell Device 014f
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Dell Device 014f
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Dell Device 014f
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=0a, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: e0200000-e02fffff
	Prefetchable memory behind bridge: 20000000-27ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Memory at 28000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Dell Device 014f
	Flags: medium devsel, IRQ 10
	I/O ports at 1880 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
	Subsystem: Conexant Systems, Inc. Device 5422
	Flags: medium devsel, IRQ 10
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0212000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0213000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 24000000-27fff000 (prefetchable)
	Memory window 1: 30000000-33fff000
	I/O window 0: 00003800-000038ff
	I/O window 1: 00003c00-00003cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04) (prog-if 10)
	Subsystem: Dell Device 014f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e0211000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Device 2561
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at e0210000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2100
	Kernel modules: ipw2100

02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
	Subsystem: Dell Device 2003
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at e0200000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

07:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Netgear Device 5b00
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at 30000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci

Second, the result from ifconfig

dave@cyclops:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6c:9d:7c:43  
          inet6 addr: fe80::214:6cff:fe9d:7c43/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3051 (3.0 KB)  TX bytes:3645 (3.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:43:3e:df  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe43:3edf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76850860 (76.8 MB)  TX bytes:2289537 (2.2 MB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:2d:f6:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x4000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-9D-7C-43-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103748 errors:0 dropped:0 overruns:0 frame:23500
          TX packets:1133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:20207292 (20.2 MB)  TX bytes:75441 (75.4 KB)
          Interrupt:10 

I am currently downloading Hardy at the moment. Once I've tested it I'll come back with the result :)

Thanks again.

---

### Post by ELF_O8 on 2009-01-07
Yeah, once I upgraded to Intrepid everything "just worked".
As tehy upgrade the OS they add in support for all kinds of drivers, including bug fixes for problems just like yours. I would advise upgrading to Intrepid (if Hardy doesn't work) and seeing if your problem still exists.

---

### Post by AP0ll0UK on 2009-01-07
I'm actually on Intrepid [8.10] at present but once I've trid Hardy [8.04] I'll report back with wireless testing results.

---

### Post by ELF_O8 on 2009-01-07
> **AP0ll0UK said:**
> I'm actually on Intrepid [8.10] at present but once I've trid Hardy [8.04] I'll report back with wireless testing results.

Oh, my bad.

---

### Post by Coombabah on 2009-01-08
> **AP0ll0UK said:**
> I'm actually on Intrepid [8.10] at present but once I've trid Hardy [8.04] I'll report back with wireless testing results.

Intrepid gave me better hardware support but (Network Manager 0.7) broke my Wireless that was happy in Hardy.

I found a workaround yesterday involving gconf-editor to manually remove ccmp entries that network-manager 0.7 keeps inserting and stopping tkip working. Whilst looking for a fix there seemed to be a few bugs with the new improved network-manager that were not in Hardy.

If you get wireless working in Hardy you have another alternative to XP or spending time sorting out your wireless issues in Intrepid when you are new to Ubuntu.

---

### Post by AP0ll0UK on 2009-01-08
I seem to have the same issue with Hardy unfortunately. 

I'm prompted to enter the key for my wireless network and it won't connect. I'm just prompted for the key again.

Does anyone have any other ideas please?

I've used various flavours of Linux in the past [many many moons ago] such as Redhat, Mandrake and Suse but not to any great length. I've no problem in following tutorials or HowTo's if anyone can please give me any pointers?

Thanks.

---

### Post by AP0ll0UK on 2009-01-08
[Edit]
Apologies for the double post, I had problems sending my last reply - forums issues this evening?
[/Edit]

---

### Post by Favux on 2009-01-08
Hi AP0ll0UK,

Here is the link to the work-a-round Coombabah talked about.  It sounds like you're having the same issue.  Are you still in Hardy or back to Intrepid?  Maybe NM 0.7 stayed when you went to Hardy?  Anyway the link:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Hope it's helpful.

---

### Post by Coombabah on 2009-01-09
> **AP0ll0UK said:**
> I seem to have the same issue with Hardy unfortunately. 

I'm prompted to enter the key for my wireless network and it won't connect. I'm just prompted for the key again.

Does anyone have any other ideas please?

I've used various flavours of Linux in the past [many many moons ago] such as Redhat, Mandrake and Suse but not to any great length. I've no problem in following tutorials or HowTo's if anyone can please give me any pointers?

Thanks.

Sorry that didn't work. At least it rules out a NM 0.7 issue.

If you haven't already looked here then this might help or steer you in the right direction.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---


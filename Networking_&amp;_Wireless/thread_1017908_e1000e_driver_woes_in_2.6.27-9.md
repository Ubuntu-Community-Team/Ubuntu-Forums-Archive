---
title: "e1000e driver woes in 2.6.27-9 ???"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by TSchultz55 on 2008-12-21
So, I finally took the plunge and upgraded from 8.04 to 8.10 today.  Everything seemed to go fine until I rebooted, and alas, discovered I couldn't get an IP address via DHCP.

I was hesitant to do the upgrade based on the e1000e driver nightmares I heard about, but figured it was fixed at this point, and decided to proceed.  I can't get my Ethernet card to work, and am unsure if this is somehow related to e1000e drivers hosing down supported hardware.  Here's a quick snapshot of the diagnosis:

1.  2.6.27-9-generic kernel
2.  Intel Corporation 82562V 10/100 Network Connection (rev 02)
3.  e1000e driver
4.  The driver DOES seem to load properly
5.  eth0 IS detected
6.  However, it is saying the link does not exist - "eth0: link is not ready"
7.  Hardware lights are not on

Here's the debugging information I can provide from my own investigation:

tim@chabrias:~$ uname -a
Linux chabrias 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
=============================================================================
tim@chabrias:~$ lspci -v | grep Ethernet -A 1
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
	Subsystem: Dell Device 01dd
=============================================================================
tim@chabrias:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown! (65535)
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: no
=============================================================================
tim@chabrias:~$ sudo ethtool -i eth0
driver: e1000e
version: 0.3.3.3-k6
firmware-version: 1.1-2
bus-info: 0000:00:19.0
=============================================================================
tim@chabrias:~$ sudo modprobe e1000e 
----------------------------------------
tim@chabrias:~$ tail -f /var/log/messages
Dec 21 13:10:30 chabrias kernel: [ 1737.593732] e1000e 0000:00:19.0: PCI INT A disabled
Dec 21 13:11:39 chabrias kernel: [ 1806.456372] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Dec 21 13:11:39 chabrias kernel: [ 1806.456379] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Dec 21 13:11:39 chabrias kernel: [ 1806.457508] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 21 13:11:39 chabrias kernel: [ 1806.546722] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:73:2c:d9
Dec 21 13:11:39 chabrias kernel: [ 1806.546728] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
Dec 21 13:11:39 chabrias kernel: [ 1806.548462] 0000:00:19.0: eth0: MAC: 4, PHY: 7, PBA No: 1021ff-0ff
===============================================================================
tim@chabrias:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:d1:73:2c:d9
Sending on   LPF/eth0/00:19:d1:73:2c:d9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
===============================================================================
tim@chabrias:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:73:2c:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dfde0000-dfe00000 
===============================================================================
tim@chabrias:~$ sudo ifconfig eth0 down
tim@chabrias:~$ sudo ifconfig eth0 up
-----------------------------------------
tim@chabrias:~$ tail -f /var/log/messages
Dec 21 13:12:16 chabrias kernel: [ 1843.713396] ADDRCONF(NETDEV_UP):  eth0: link is not ready
===============================================================================
tim@chabrias:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:73:2c:d9
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:74:65:fe:18:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
================================================================================
tim@chabrias:~$ sudo ethtool -e eth0
Offset		Values
------		------
0x0000		00 19 d1 73 2c d9 00 08 ff ff 12 10 ff ff ff ff 
0x0010		21 10 ff ff c7 10 dd 01 28 10 4c 10 86 80 00 00 
0x0020		02 04 00 00 00 00 85 96 20 40 00 00 00 00 07 00 
0x0030		84 06 41 03 00 00 00 00 00 00 00 00 00 00 00 00 
0x0040		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x0050		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x0060		00 01 00 40 28 12 07 40 ff ff ff ff ff ff ff ff 
0x0070		ff ff ff ff ff ff ff ff ff ff ff ff ff ff 59 01 
0x0080		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x0090		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
0x00a0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x00b0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x00c0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
...
...  (all 'ff')
...
0x0f50		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0f60		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0f70		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0f80		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0f90		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0fa0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0fb0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0fc0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0fd0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0fe0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
0x0ff0		ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
==============================================================================
tim@chabrias:~$ cat /proc/iomem
00000000-0009c3ff : System RAM
000a0000-000bffff : Video RAM area
000c0000-000c7fff : Video ROM
000cd000-000d0fff : Adapter ROM
000d1000-000d3fff : Adapter ROM
000f0000-000fffff : reserved
  000f0000-000fffff : System ROM
00100000-7f651bff : System RAM
  00100000-00383359 : Kernel code
  0038335a-004a567f : Kernel data
  00515000-005c0a1f : Kernel bss
7f651c00-7f653bff : ACPI Non-volatile Storage
7f655c00-7f657bff : ACPI Tables
7f657c00-7fffffff : reserved
88000000-88000fff : Intel Flush Page
c0000000-cfffffff : 0000:00:02.0
dfb00000-dfbfffff : PCI Bus 0000:02
dfc00000-dfcfffff : PCI Bus 0000:01
dfddab00-dfddabff : 0000:00:1f.3
dfddac00-dfddafff : 0000:00:1a.7
  dfddac00-dfddafff : ehci_hcd
dfddb000-dfddbfff : 0000:00:19.0
  dfddb000-dfddbfff : e1000e
dfddc000-dfddffff : 0000:00:1b.0
  dfddc000-dfddffff : ICH HD audio
dfde0000-dfdfffff : 0000:00:19.0
  dfde0000-dfdfffff : e1000e
dfe00000-dfefffff : 0000:00:02.0
dff00000-dfffffff : 0000:00:02.1
e0000000-efffffff : PCI MMCONFIG 0
  e0000000-efffffff : reserved
fec00000-fed003ff : reserved
  fed00000-fed003ff : HPET 0
fed20000-fed9ffff : reserved
feda0000-fedacfff : pnp 00:07
fee00000-feefffff : reserved
  fee00000-fee00fff : Local APIC
ff970000-ff9707ff : 0000:00:1f.2
  ff970000-ff9707ff : ahci
ff980800-ff980bff : 0000:00:1d.7
  ff980800-ff980bff : ehci_hcd
ffb00000-ffffffff : reserved

This is unfortunately starting to get out of the scope of my Linux knowledge.  Any help would be GREATLY appreciated.  This box serves as my home Subversion server, and it basically my LIFELINE!

Thoughts?  Thank you all and have a happy holiday!

Cheers,

Tim

---

### Post by pytheas22 on 2008-12-21
I think the e1000e issues were worked out well before the stable release of 8.10.

Maybe e1000e just doesn't support your card?  Could you just instead use the module that had it working under 8.04 (which I presume is e1000), i.e.:
```

sudo rmmod e1000e
sudo modprobe e1000
sudo ifconfig eth0 up
sudo dhclient eth0
```

Does that work?

---

### Post by TSchultz55 on 2008-12-21
Hi pytheas22, thanks for the quick response!

If I rmmod e1000e, eth0 suddenly disappears.  modprobe e1000 doesn't bring it back:

eth0: ERROR while getting interface flags: No such device.

I'm guessing e1000e is in fact the correct driver to be using?

---

### Post by pytheas22 on 2008-12-21
> I'm guessing e1000e is in fact the correct driver to be using?

You would think, but it's hard to be sure.  If you have an 8.04 live CD handy, could you boot to it quickly and see which module is used to drive your ethernet card there?  Look at the output of 'lshw -C Network' or 'lsmod' to figure it out.

Also, what is the 'lspci -nn' line for your ethernet card?

---

### Post by TSchultz55 on 2008-12-21
pytheas22,

tim@chabrias:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82P965/G965 Memory Controller Hub [8086:29a0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82P965/G965 PCI Express Root Port [8086:29a1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G965 Integrated Graphics Controller [8086:29a2] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82G965 Integrated Graphics Controller [8086:29a3] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V 10/100 Network Connection [8086:104c] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller [8086:2812] (rev 02)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)


And that brings me to another little problem.  CD-ROM drive can't be found either.  Doesn't open when I press the button.  Aurgh.  So a LiveCD at the moment isn't possible.

While I work on that, if we assume either: e1000 IS the correct driver, why would eth0 not be present or if e1000e is the correct driver, why wouldn't the link be enabled?

Thoughts as to how to proceed?  Not having such good luck here.....

Thanks!

Tim

---

### Post by pytheas22 on 2008-12-21
> While I work on that, if we assume either: e1000 IS the correct driver, why would eth0 not be present or if e1000e is the correct driver, why wouldn't the link be enabled?

Good question.  Maybe dmesg will provide some clues as to what's going on, with both e1000e and e1000.  What is the output of:
```

sudo modprobe e1000e
dmesg | grep -e 1000 -e eth
sudo rmmod e1000e
sudo modprobe e1000
dmesg | grep -e 1000 -e eth
```

In the meantime, I'll google around for your ethernet card's PCI ID (8086:104c) + e1000e to see what turns up.

---

### Post by TSchultz55 on 2008-12-21
pytheas22, appreciate the help.  I've been Googling all sorts of combinations of error messages/outputs/hardware info all day with no success.  Anything you can find would be amazing.  :)

As for dmesg output, I don't see too much in it that could definitively point to a cause.  Here's what I COULD find:

Dec 21 13:10:30 chabrias kernel: [ 1737.593732] e1000e 0000:00:19.0: PCI INT A disabled
Dec 21 13:11:39 chabrias kernel: [ 1806.456372] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Dec 21 13:11:39 chabrias kernel: [ 1806.456379] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Dec 21 13:11:39 chabrias kernel: [ 1806.457508] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 21 13:11:39 chabrias kernel: [ 1806.546722] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:73:2c:d9
Dec 21 13:11:39 chabrias kernel: [ 1806.546728] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
Dec 21 13:11:39 chabrias kernel: [ 1806.548462] 0000:00:19.0: eth0: MAC: 4, PHY: 7, PBA No: 1021ff-0ff

modprobe e1000 seems to have no effect whatsoever on the system.

Again, this is starting to go beyond my knowledge of Linux: only thing I noticed is "PCI INT A disabled".

---

### Post by pytheas22 on 2008-12-21
I still haven't turned up anything definitive, but according to [this page]("http://cateee.net/lkddb/web-lkddb/E1000.html"), e1000 should be able to drive your card (if you search for the PCI ID on that page, it says that it's one of the devices supported by e1000).  I wonder if e1000 is failing to take control because e1000e is not really being removed?  What is the output of this, in this order:
```

lsmod | grep 1000
sudo rmmod e1000e
lshw -C Network
sudo modprobe e1000
dmesg | tail
lsmod | grep 1000
lshw -C Network
```

---

### Post by TSchultz55 on 2008-12-21
I have no clue what just happened.  I rmmod and modprobe e1000e one last time (as I've been doing all day) and suddenly the network manager icon in the top right (Gnome) changed to the two green dots inside a swirling blue circle when it does a DHCP request.  I'm actually posting this from it now.

This makes no sense.  It's working but it's horrifically slow.  This is connected to a Synergy server to share a keyboard and mouse and the mouse skips across the screen.  But looks like we're getting somewhere.

Here's a snapshot of the configuration with it miraculously working:

tim@chabrias:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:73:2c:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 ip=192.168.1.2 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s

tim@chabrias:~$ sudo ethtool -i eth0
driver: e1000e
version: 0.3.3.3-k6
firmware-version: 1.1-2
bus-info: 0000:00:19.0

tim@chabrias:~$ lsmod | grep 1000
e1000e                112680  0 
e1000                 132164  0 

tim@chabrias:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

tim@chabrias:~$ dmesg | tail
[26926.655211] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[26926.655221] e1000e 0000:00:19.0: setting latency timer to 64
[26926.742985] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:73:2c:d9
[26926.742993] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[26926.743078] 0000:00:19.0: eth0: MAC: 4, PHY: 7, PBA No: 1021ff-0ff
[26930.828414] ADDRCONF(NETDEV_UP): eth0: link is not ready
[26932.468799] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[26932.468806] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[26932.470575] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[26943.388047] eth0: no IPv6 routers present

So it's working now with e1000e.  I wonder what happens if I reboot?

Thanks!!!

Tim

---

### Post by TSchultz55 on 2008-12-21
Some more testing to see why the crappy speeds with e1000e and this NIC.  Since it's connected to a Synergy server, I used Wireshark to see what's happening at the packet level.  

Pretty much every packet to or from the box in question is showing up in Wireshark as TCP CHECKSUM INCORRECT (about 95% of the time).

Odd.

---

### Post by pytheas22 on 2008-12-21
Glad to hear that you finally got an IP.  Strange that it works all of a sudden.  I do notice some interesting differences in the output of 'ethtool eth0' now that it's working, however--in particular, none of the lines read 'Unknown!' any longer.  Don't know if this would be related to the problem or not.

> 
Pretty much every packet to or from the box in question is showing up in Wireshark as TCP CHECKSUM INCORRECT (about 95% of the time).

I was dealing with an old NIC that was doing the same thing the other day (but interestingly, only with ssh packets).  It turned out to be happening because the NIC was trying to compute the checksums.  Telling the CPU to do it instead fixed the problem.  I had to run this command:
```

sudo ethtool -K eth0 rx off tx off
```

as per [this post]("http://chungdh2.blogspot.com/2008/06/tcpdump-how-to-fix-bad-checksum-problem.html").

I have no idea if this will help in your situation, but it's worth a try.

If that doesn't work, there must be some way to tell the kernel not to worry about checksums, although I don't know whether that's a good idea...

---

### Post by TSchultz55 on 2008-12-21
Hey pytheas22,

1.  For some reason, it seems like if I rmmod e1000e and modprobe e1000e, eth0 will NOT work until I put the box into Hibernation mode and then take it out of hiberation.  When it comes out of hibernation, the NIC seems to come to life and request an IP.  I've recreated this a few times.  Not sure why this is.

2.  As for the crappy performance, I think this may have to do with IPv6.  The upgrade for some reason turned it back on.  Disabling IPv6 support seemed to do the trick in this case, as the box is very responsive now with Synergy.

Now the last problem is that [http://chabrias](http://chabrias) & [http://192.168.1.2](http://192.168.1.2) or [http://localhost](http://localhost) & [http://127.0.0.1](http://127.0.0.1) do not work with apache2 running.  I can start and stop apache2 service without issue or errors.  Do you think this is related somehow?

Thanks for the help!  Much appreciated.

Regards,

Tim

---

### Post by pytheas22 on 2008-12-22
> 1. For some reason, it seems like if I rmmod e1000e and modprobe e1000e, eth0 will NOT work until I put the box into Hibernation mode and then take it out of hiberation. When it comes out of hibernation, the NIC seems to come to life and request an IP. I've recreated this a few times. Not sure why this is.

That seems quite strange.  The only thing I can think of is that something in one of the resume scripts could be doing the trick to make the card work again?  Is there anything in /usr/lib/pm-utils/sleep.d that looks like it would be related?
> 
Now the last problem is that [http://chabrias](http://chabrias) & [http://192.168.1.2](http://192.168.1.2) or [http://localhost](http://localhost) & [http://127.0.0.1](http://127.0.0.1) do not work with apache2 running. I can start and stop apache2 service without issue or errors. Do you think this is related somehow?

That's weird too.  Have you tried looking at the packets (probably would need to watch interface 'lo') to see what's happening?  Can you access your Apache server from other machines in the house?

---

### Post by xefialtis on 2009-03-24
I am having some similar problems with 8.04 Server where I have 2 of the e1000 cards installed.

Everything seems to be installed:
> 
lshw -C Network
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82541PI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth2
       version: 05
       serial: 00:1b:21:04:37:71
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=32 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:2 DISABLED
       description: Ethernet interface
       product: 82541PI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:1b:21:04:37:95
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=32 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair

> 
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) [8086:2530] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge [8086:2532] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 04)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 04)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 04)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
02:01.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 74)
02:03.0 Ethernet controller [0200]: Intel Corporation 82541PI Gigabit Ethernet Controller [8086:107c] (rev 05)
02:04.0 Ethernet controller [0200]: Intel Corporation 82541PI Gigabit Ethernet Controller [8086:107c] (rev 05)
02:06.0 Mass storage controller [0180]: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N [1103:0004] (rev 04)

But when I plug in the cable, and request DHCP, I get the following:
> 
 ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:21:04:37:95
Sending on   LPF/eth1/00:1b:21:04:37:95
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The LIGHTS are ON (but no one is home, I guess)...
and the cable I am using is a known "good" cable (I have tried 2 of them, no success, and they both work fine with other machines).

Do you have any ideas or suggestions to get these e1000 cards running?

Or do I go with Plan B and buy a couple 3Com cards?

---

### Post by pytheas22 on 2009-03-24
**xefialtis**: both interfaces are listed as 'disabled', which did not occur for the original poster in this thread, so I'm not sure the problems are the same (your ethernet card is also not the same model as TSchultz55's).

I would first kill NetworkManager ('sudo /etc/init.d/NetworkManager stop') so that it doesn't interfere with anything, then bring the interfaces up with 'sudo ifconfig eth0' up (same for eth1).  At this point, does 'lshw -C Network' still say they're disabled?  Can you get an IP using dhclient?

You might also have better luck if you rmmod the e1000 module and load e1000e instead.  I'm not sure if it supports your card, but it might.

---

### Post by xefialtis on 2009-03-25
I think I have it partially fixed, and it is a weird issue.
WHen I enable the devices (I know it says it was disabled, I hadn't run ifup at that point) they say (via ethtool) there is no link detected (even though the lights come on on the card).

I tried a crossover cable.

It fixed that issue, but I still don't know if it will work for the WAN side. I will be getting some more cross-over cables tonight to see if I can get both to come up and link and register DHCP...

Stay tuned...

Just as soon as I upgrade to 8.10, I will change the drivers to the e1000e, and I also bought a couple 3C200-LP (3com) cards to try...

---

### Post by blindchimp on 2009-08-19
i had problems with e1000e going from 2.6.27-11 to -14 .
turned out in -14, they REVERTED the e1000e driver back to version 0.3.3.3-k6,
which didn't even detect my chipset. in -11, the version was 0.5.18.3-NAPI
which worked fine. it appears the old 0.3.3.3 driver is in 9.04 as well.

i'm going to try rebuilding the driver from the latest intel sources and see if
that works.

---

### Post by blindchimp on 2009-08-19
yep, appears to work now. the version of the driver from intel (1.0.2.5-NAPI) finds my chipset
no problem using the -14 kernel. it also appears to find my second ethernet port (eth1) properly, 
which the previous driver did not.

---


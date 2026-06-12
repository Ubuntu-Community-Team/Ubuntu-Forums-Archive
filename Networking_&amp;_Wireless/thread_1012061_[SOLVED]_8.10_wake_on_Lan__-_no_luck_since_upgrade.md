---
title: "[SOLVED] 8.10 wake on Lan  - no luck since upgrade from hardy"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by barkerben on 2008-12-15
Hi, I have read the various wol threads. I was using wol fine in Hardy, but in 8.10 I have been stumped. 

I have onboard ethernet, according to lspci:

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

To test wake, I am using another machine on the network with:

sudo etherwake -b MACADDRESS_OF_SHUTDOWN_MACHINE

ethtool eth0 gives:

	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes



I have also added this to the /etc/rc.local file:
ethtool -s eth0 wol g

I have also checked the BIOS, and wol is enabled 

I also found this:

[http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex](http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex)

Which I tried, to no effect. I noted that in the above link, it states that I  should change NETDOWN=yes to NETDOWN=no...but there was no such line in my file. I added it anyway...no luck :-p

After that, I used wireshark to verify that the broadcast packet is being broadcast, which it is...

As a final check, I booted into windows 9which I rarely do) and first shutdown, then hibernated the PC. From both the shutdown and the hibernated states I was able to wol, confirming my problem lies somehwhere with the state Ubuntu leaves the machine in when it shuts down...


Any thoughts?

---

### Post by barkerben on 2008-12-16
After looking at my dmesg, this was confirmed:

[    3.297594] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.298083] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    3.298135] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    3.298197] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.298219] nv_probe: set workaround bit for reversed mac addr
[    3.540026] usb 1-7: new high speed USB device using ehci_hcd and address 7
[    3.811800] usb 1-7: configuration #1 chosen from 1 choice
[    3.821479] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:17:31:cb:19:6a

and also

[   34.445473] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.445482] apm: disabled - APM is not SMP safe.


assuming apm is advanced power management, I wonder if this could be relevant...

---

### Post by barkerben on 2008-12-17
I wonder whether this could have any bearing:

[http://www.mail-archive.com/netdev@vger.kernel.org/msg39392.html](http://www.mail-archive.com/netdev@vger.kernel.org/msg39392.html)

Unsure what it is talking about, but will investigate...

---

### Post by barkerben on 2008-12-18
Fixed :-)

Initially I tried using a broadcast IP (255.255.255.255) and a reversed MAC -no joy.

Then I upgraded my network manager, and tried again...

It works :-)

A unicast IP does not work however, and neither does a non-reversed MAC. Shutting down from windows this does work, so there is something odd still going on...

---

### Post by evenstranger on 2008-12-18
Hi, I have been through a similar process, followed these instructions :
[http://sethbc.org/2008/10/12/wake-on...-intrepid-ibex](http://sethbc.org/2008/10/12/wake-on...-intrepid-ibex)

And also added the line to /etc/rc.local. I haven't been able to fix the problem. Could you describe the steps you took to upgrade network manager and the wakeonlan command that you issue to get it to work ? Any help would be much appreciated.

---

### Post by barkerben on 2008-12-18
The upgrade of network manager was a bit of a fluke. Normally Ubuntu lets me know when it has some updates for me, but last night I went explicitly to the "Updates" screen (under System--->administration I think) and did a search for updates. 

A few were found, and one of them was for network manager. 

I now use php to wake my machine, but during testing used etherwake. 

If this is not installed, it can be from the repositories (apt-get install etherwake)

then do etherwake -b YOUR_MAC_ADDRES_IN_REVERSE

(-b specifies a broadcast packet)

for example if your mac address is a1:b2:c3:d4:e5:f6

then use etherwake -b f6:e5:d4:c3:b2:a1

It seems this mac reversal is a know bug with the forcedeth driver. As for the need to use a broadcast packet, I don't know why that is - nother bug I assume (since when shutting down from windows I don't need to)

I did find some people talking about this problem and offering patches, but it was a bit above my head and I didn't want to risk breaking my kernel, so I decided just to live with the situation, since I can work around it.

---

### Post by evenstranger on 2008-12-20
thanks for the response barkerben, reversing the mac id has got it all working. cheers.

---

### Post by barkerben on 2009-03-04
...I changed to a new motherboard, and my problems returned. Then I removed network manager completely and replaced it with "wicd" - now everything just works, and the network is a lot easier to configure too :-)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by waster on 2009-03-09
I've made a very simple change to the forcedeth kernel module, and this ppa package uses dkms to rebuild it automatically. you can change the numbers in my patch to set a fixed mac address if forcedeth gets it wrong.

[http://ppa.launchpad.net/waster/ppa/ubuntu](http://ppa.launchpad.net/waster/ppa/ubuntu)

---


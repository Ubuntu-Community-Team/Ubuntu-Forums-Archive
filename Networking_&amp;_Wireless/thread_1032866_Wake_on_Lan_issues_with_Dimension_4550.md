---
title: "Wake on Lan issues with Dimension 4550"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by mbshah on 2009-01-06
Folks,
I have a Dimension 4550 and I am trying to bring it up by sending a magic packet. It has an onboard Intel ethernet controller Pro/100. Here is what I have tried so far:

1) Ensured my machine supports wol function by testing it on windows partition.
2) I have 8.10 installed. I added 
ethtool -s eth0 wol g
to /etc/rc.local as recommended by this posting:
[http://ubuntuforums.org/archive/index.php/t-360901.html](http://ubuntuforums.org/archive/index.php/t-360901.html)

When I follow up with 
ethtool eth0
it checks out


root@mihir-desktop:/home/mihir# ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes
 

mihir@mihir-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


I also tried creating a file called wakeonlanconfig with the above statement as recommended by this posting:
[http://www.averyjparker.com/ubuntu-linux/](http://www.averyjparker.com/ubuntu-linux/)

However, as soon as I shutdown the LED next to the ethernet connector goes off - which stays on when I shutdown with windows.

I also looked at the /proc/acpi/wakeup, however I 
I don't see the ethernet controller in /proc/acpi/wakeon

root@mihir-desktop:/home/mihir#
Device	S-state	  Status   Sysfs node
VBTN	  S4	*enabled   
PCI0	  S3	 disabled  no-bus:pci0000:00
USB0	  S3	 disabled  pci:0000:00:1d.0
USB1	  S3	 disabled  pci:0000:00:1d.1
USB2	  S3	 disabled  pci:0000:00:1d.2
PCI1	  S5	 disabled  pci:0000:00:1e.0
KBD	  S3	 disabled  pnp:00:06

So I cannot enable it.

Can anyone suggest how I can keep the network controller enabled when I shutdown the computer?

Thanks

---

### Post by mbshah on 2009-01-11
It seems there is some issue with 8.10. I installed 8.04 and used the same steps and the pc wakes up from shutdown/halt/suspend.

---

### Post by gaggia on 2009-12-14
Does WOL still work for you?  I inherited a 4550 (my gamer son got a newer machine) and I can't get WOL to work with Ubuntu 9.04 or 9.10.  I can set and see the 'g' in ethtool, and the LEDs adjacent to the built-in Ethernet connector stay on when the machine is is in suspend mode.  Pressing the power button in suspend mode wakes up the machine (about five seconds to the Ubuntu splash screen; no booting).

(BTW, those Ethernet LEDs didn't stay on when running 9.04.)

I'm sending magic packets from my Linux-based router machine (not Ubuntu).  If I'm logged into the 4550, I can run tcpdump port 40000 (default port for magic packets on the router box), and I can see the magic packets; I can dump them with tcpdump -xx -XX too.  But with all of the above working, the 4550 won't wake on lan.

What am I missing?

Thanks in advance.

---


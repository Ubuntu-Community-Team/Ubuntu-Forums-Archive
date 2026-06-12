---
title: "Wake on LAN not working under server 11.10"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by legendli on 2011-12-08
Hi All, 

I have a Dell Precision t3400 workstation installed with Ubuntu server 11.10 64bit as a headless NAS . This machine works pretty good except WOL.  

I tried almost all solutions that I can find through google, such as using:

1. ethtool enable NIC wake on LAN

2. Enable my NIC PCI device for S5 wakeup

3.Set NETDOWN=NO in /etc/init.d/halt

BUT no lucky the server still can't be waked  up. 

For my first understanding, WOL is only related the BIOS, but if I shutdown this Dell workstation by another disk that installed Windows7, WOL is working all the time. So I believe there is nothing wrong with the BIOS settings.

However, If I shutdown the machine with Ubuntu server, then WOL doesn't work at all. Though I saw the led is flashing on the switch after shutting down.  With ethereal, I can saw the magic package.

Please, if anyone have the same issue please please just share some information. 
THANKS A LOT!

---

### Post by SteveDee on 2011-12-08
> **legendli said:**
> ...For my first understanding, WOL is only related the BIOS, but if I shutdown this Dell workstation by another disk that installed Windows7, WOL is working all the time. So I believe there is nothing wrong with the BIOS settings....

So it looks like your BIOS and your network card are OK.

Its been 2 or 3 years since I played around with wake-on-lan but here are notes from my personal wiki:-
> 
**++++Wake On LAN**
Go to bios and enable the “Wake On Lan”
Then:-
sudo apt-get install wakeonlan

This command only work on tv rec computer when left connected to power after a power down (draws 5Watts):-
wakeonlan -i 200.1.1.255 00:19:db:25:a7:03
...only when wake support has been turned on using ethtool...as this setting resets each time it re-boots from a wake...is there a setting in BIOS that is clearing it?
So to keep wake-up mode I run a script at start up:-
#!/bin/sh
ethtool -s eth3 wol g

...the ethtool command has been set suid by:-
sudo chmod u+s /usr/sbin/ethtool

**++++Check WakeUp capabilities of network card**
use command;
sudo ethtool ethx  {where x is actual interface}
shows:-
Supports Wakeon: {options}
Wakeon: {wol options}
wol p|u|m|b|a|g|s|d...
   Set Wake-on-LAN options.  Not all  devices  support this.       The argument  to  this  option  is a string of characters specifying
              which options to enable.
              p  Wake on phy activity
              u  Wake on unicast messages
              m  Wake on multicast messages
              b  Wake on broadcast messages
              a  Wake on ARP
              g  Wake on Magicpacket(tm)
              s  Enable Secureon(tm) password for Magicpacket(tm)
              d  Disable (wake on nothing).  This option clears  all  previous options.


...so I suggest you create the simple startup ethtool script (above) if you haven't already tried this.

---

### Post by papibe on 2011-12-08
Have you take a look at this [tutorial]("https://help.ubuntu.com/community/WakeOnLan")?

Regards.

---

### Post by legendli on 2011-12-09
Thanks for your replay, 
 
Let me put more details, 
 
I'm using a Cisco Linksys WRT610N with DD-WRT to send the magic package, it's working with my another Dell workstation T3500 of cause it's Windows Base. So I believe the DD-WRT works good. 
 
Below is my ethtool result:
> Settings for eth0:
Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Half 1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Half 1000baseT/Full 
Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: g
Wake-on: g
Current message level: 0x000000ff (255)
drv probe link timer ifdown ifup rx_err tx_err
Link detected: yes
 
and my /proc/acpi/wakeup
> Device S-state Status Sysfs node
VBTN S4 *enabled 
PCI0 S5 *disabled no-bus:pci0000:00
PCI4 S5 *enabled pci:0000:00:1e.0
PCI3 S5 *disabled 
PCI1 S5 *disabled pci:0000:00:01.0
PCI6 S5 *disabled pci:0000:00:1c.5
USB0 S3 *disabled pci:0000:00:1d.0
USB1 S3 *disabled pci:0000:00:1d.1
USB2 S3 *disabled pci:0000:00:1d.2
USB3 S3 *disabled pci:0000:00:1a.0
USB4 S3 *disabled pci:0000:00:1a.1
USB5 S3 *disabled pci:0000:00:1a.2
 
and result of lspci -k
 
> 04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Dell Precision T3400
        Kernel driver in use: tg3
        Kernel modules: tg3

---

### Post by Gordon D on 2011-12-15
SteveDee's answer is right on the money. Having spent a few hours trying to sort this out yesterday! :)

So much of what you read on this subject seems to be irrelevant or out of date. The forums are great, but there should be a way of marking posts as "complete c**p - please ignore" :D

I would stress that the power needs to be connected to the PC all the time. I tested multiple WOL's and they worked fine, but when I moved the PC to the basement it stopped working. If you move the PC, or if there is a power outage, you have to do a manual boot the first time.

This may not be a problem if you card defaults to "g" on boot up without use of the ethtool, but if that is the case there should be few problems in getting WOL to work.

As an observation and in my limited experience only, Windows does seem to handle this better ... when you update the network card driver setting in Windows to allow WOL, it seems to "stick" in NVRAM. This could be c**p though, so please ignore :D

Great when it works though. :D

Gordon

---


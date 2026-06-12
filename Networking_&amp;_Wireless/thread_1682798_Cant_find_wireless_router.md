---
title: "Cant find wireless router"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by andywhoa on 2011-02-06
Ubuntu 10.04 x86

Yesterday I installed 10.10 and had lots of trouble with wireless stability.  I formated the partition and installed 10.04.

New problem:  My wireless router does not show up in the available routers list......  Neither in the list that immediately shows or under the More networks submenu.  Lots of other routers from adjacent homes show up, but not mine in the other room.

Why?  It shows up on all of my other computers.  My MacBook, Windows 7 (different partition on same box), my older Ubuntu netbook, and it showed up on a previous install of 10.10 (though it could not maintain the connection longer than 5 minutes).  It will not show up on Ubuntu 10.04.

I've tried manually entering the information to connect, but it doesn't see it.  I don't know what to do.

---

### Post by andywhoa on 2011-02-06
I don't mean to be disrespectful, but it is truly unbelievable how problematic establishing a wireless connection with Ubuntu has become.  This is one of those pivotal areas you think would be highly scrutinized before trying to garner new users.

---

### Post by TBABill on 2011-02-06
Is it because this computer has a different model wireless device? They do not all work out of the box and may need a driver setup, just like in Windows. Most are easy enough to get going.

Can you enter this in a terminal and provide the output ```
lscpi
``` and ```
sudo lshw -C network
```

---

### Post by andywhoa on 2011-02-06
Thank you for your response

I'm not quite sure why this computer's wireless adapter would have anything to do with my router not showing up.  Like I said, lots of routers show up, just not mine.  If there was an issue with my wireless adapter seeing wireless routers, how is anything showing up at all?

There may indeed be an issue with actually connecting my wireless adapter to a wireless router, but that's a separate matter.  Right now I need to figure out why my router is gone when I see everyone else's (and all of my other Linux, OS X and Windows installs see it just fine).

Here is some terminal output:



Result of lspci
> 
00:00.0 Host bridge: nVidia Corporation Device 0800 (rev b1)
00:00.1 RAM memory: nVidia Corporation Device 0808 (rev a1)
00:00.2 RAM memory: nVidia Corporation Device 0809 (rev a1)
00:00.3 RAM memory: nVidia Corporation Device 080a (rev a1)
00:00.4 RAM memory: nVidia Corporation Device 080b (rev a1)
00:00.5 RAM memory: nVidia Corporation Device 080c (rev b1)
00:00.6 RAM memory: nVidia Corporation Device 080d (rev a1)
00:00.7 RAM memory: nVidia Corporation Device 080e (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 080f (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0810 (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0811 (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 0812 (rev a1)
00:01.4 RAM memory: nVidia Corporation Device 0813 (rev a1)
00:01.5 RAM memory: nVidia Corporation Device 0814 (rev a1)
00:01.6 RAM memory: nVidia Corporation Device 081a (rev a1)
00:01.7 RAM memory: nVidia Corporation Device 080e (rev a1)
00:02.0 PCI bridge: nVidia Corporation Device 0815 (rev a1)
00:04.0 PCI bridge: nVidia Corporation Device 0817 (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 280] (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 280] (rev a1)
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)












Result of sudo lshw -C network
>   *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:d1:50:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn







Result of route
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface



Thanks for your help

---


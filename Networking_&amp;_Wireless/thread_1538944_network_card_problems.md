---
title: "network card problems"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by morgan.wagner on 2010-07-25
I installed xubunto 10.4 on my pc the other day and every thing was working fine and then the next day my wired network card went down. So i restarted it and it say Wired Network Disconnected.

i tryed doing sudo ifconfig eht0 up. to try and bring the card back on line but nothing happens. I also tryed reinstalling xubuntu on my computer. Again my internet works then starts freezing up so i restart it and my ether net card goes down again. I have tryed also pluging it into the second ether net port on my computer but that does not seem to work.

Also i went into my dhclient-script and went to the bottom to look at my network card stuff.

it reads 
  #Changed from 'ifconfig $interface inet 0 down' - see Debian bug #144666 ifconfig $interface inet 0
   exit_with_hooks 2 "$@"
fi

i hope some one has had this problem and fixed it and can tell me what to do thanks

---

### Post by Iowan on 2010-07-26
It's been awhile since my Xubuntu machine died, so I don't remember if it had Network Manager. If it does, right-click the NM icon and verify "Networking enabled" box is checked. A couple more threads to check:
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")

---

### Post by morgan.wagner on 2010-07-26
ok my network connection are enable. 

I tryed doing

sudo  service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

it does it thing but then still i wont come up.

then i went into terminal and did 

sudo lshw -C network

and i got 

*-network DISABLED
	description: Ethernet interface
	product: RTL8111/8168B PCI Express Gigabit Ethernet controller
	vender: Realtek Semiconductor Co., Ltd
	physical id: 0
	bus info: pci@0000:03:00.0
	logical name: eth1
	version: 03
	serial:40:61:86:60:6f:49
	width: 64bits
	clock: 33MHz
	capabilities: bus_master cap_list rom ethernet physical
	configuration: broadcast=yes driber=r8169 driverversion=2.3LK-NAPI latencey=0 multicast=yes

*-network DISABLED
	description: Ethernet interface
	product: RTL8111/8168B PCI Express Gigabit Ethernet controller
	vender: Realtek Semiconductor Co., Ltd
	physical id: 0
	bus info: pci@0000:03:00.0
	logical name: eth0
	version: 03
	serial:40:61:86:60:6f:49
	width: 64bits
	clock: 33MHz
	capabilities: bus_master cap_list rom ethernet physical
	configuration: broadcast=yes driber=r8169 driverversion=2.3LK-NAPI latencey=0 multicast=yes

---


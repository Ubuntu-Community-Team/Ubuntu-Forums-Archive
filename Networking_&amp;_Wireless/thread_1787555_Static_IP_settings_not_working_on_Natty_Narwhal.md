---
title: "Static IP settings not working on Natty Narwhal"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by yasudevil on 2011-06-21
Hello,

I'm currently trying to setup a static IP address for my computer, but everytime I set the static IP my network does not works.



My lspci -v shows the follow.
```
Ethernet controller 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 7529
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at e800 [size=256]
	Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Memory at fdfe0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8101
	Kernel modules: r8101
```

In the beginning the driver that was in use was the r8169, I changed because I read in this forum that the r8169 driver has some issues.

I tried to configure the static IP address using the gnome network configurator but it didn't worked either. I removed it and tried to edit the following config files.

/etc/networks/interfaces
which looks like follow
```

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 10.193.227.92
netmask 255.255.255.0
gateway 10.193.227.1
```

I've added the valid DNS servers on /etc/resolv.conf also. 

Even after restart the system my network only works when I use dhpc to resolve my IP Address.

Does anyone know what else can I try?

---

### Post by miaviator278 on 2011-06-21
I have the same issue.  It looks like a bug in Narwhal.

---

### Post by yasudevil on 2011-06-21
Bug really? Oh god... 

I also tried to boot the Live CD version of 10.10 in the mentioned computer and changed to static IP using the gnome tools and didn't worked either.

Actually I even tried to do the same in my laptop which is running Ubuntu 10.10 and the same problem has occurred.

I didn't tried to change the driver of the network card or anything, just plain configuration using the Gnome tool.

---

### Post by collisionystm on 2011-06-21
Once you set yourself a static address, you do need to reload your network connection. Just click on your network icon and hit AUTO ETH**

You can manually check to see if your settings took by looking at

/etc/network/interfaces

Oh and BTW your file should look like this

> auto lo 
iface lo inet loopback
 auto eth0
 iface eth0 inet static 
address 10.193.227.92 
netmask 255.255.255.0 
gateway 10.193.227.1

---

### Post by collisionystm on 2011-06-21
And you do not need to reset your computer after making changes. Just

/etc/init.d/networking restart

---

### Post by yasudevil on 2011-06-21
Actually I removed the gnome network manager so it doesn't appear anymore.

I changed the setting and it shows on /etc/network/interfaces but even though ifconfig shows everything with the correct IP I can't reach any other IPs inside my network.

---

### Post by lerrow on 2011-06-23
I'm having the same issue, just runing /etc/init.d/networking restart fixes it, but I'm not always near the computer or in the office to run it. I tried removing the network-manager, the dhcp client, but I'm still having the same issue.

---


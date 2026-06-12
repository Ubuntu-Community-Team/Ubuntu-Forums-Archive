---
title: "Help: Natty x86 Ethernet Issue"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by ngrieb on 2011-09-06
I am having a serious issue with my ethernet port not registering itself on a hard boot. If I restart my computer my ethernet works. I attempted to look this issue up but after messing with some /etc/netwok/interfaces etc, I seem to have now broken the link between the network manager and what is happening in the background as well. Right now the network manager doesn't realize that I am connected but here is what I have as far as the technical stuff goes:

```

Ethernet controller from lspci:

00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)

ifconfig

eth0      Link encap:Ethernet  HWaddr 70:71:bc:99:aa:36  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe99:aa36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:317119 (317.1 KB)  TX bytes:41546 (41.5 KB)
          Interrupt:20 Memory:f9ec0000-f9ee0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

/etc/network/interfaces file looks like this right now:

auto eth0
iface eth0 inet dhcp

```

Please help, I have never had this happen before, and it is driving me insane. I know it has to be something simple.

Thanks in advance.

---

### Post by ngrieb on 2011-09-07
Is the loopback supposed to encompass the eth0 statement like in programming perhaps?

```

auto lo

auto eth0
iface eth0 inet dhcp

iface lo inet loopback

```

---

### Post by ngrieb on 2011-09-11
Um, got back the network manager by only putting the loopback into the /etc/network/interfaces config file, but I still have to restart once before I have a connection... anybody know why?

If I do an lspci -v I get:

DOWN-------------------------------------------------------------------------------------------
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
	Subsystem: eVga.com. Corp. Device 0075
	Flags: fast devsel, IRQ 20
	Memory at f9ec0000 (32-bit, non-prefetchable) [size=128K]
	Memory at f9efc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at dc00 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [e0] PCI Advanced Features
	Kernel modules: e1000e

UP--------------------------------------------------------------------------------------------
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
	Subsystem: eVga.com. Corp. Device 0075
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f9ec0000 (32-bit, non-prefetchable) [size=128K]
	Memory at f9efc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at dc00 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] PCI Advanced Features
	Kernel driver in use: e1000e
	Kernel modules: e1000e

Nothing really different here except the enable, is there a way to enable through some config file?

---

### Post by ngrieb on 2011-09-17
Please...Anyone??? This is really starting to frustrate me. Why would my eth0 config only run if I first boot ant then restart? What is different about restarting and rebooting? 

Still nothing....? Could it be my BIOS, or is it software issue? Is there anything I can try?

---


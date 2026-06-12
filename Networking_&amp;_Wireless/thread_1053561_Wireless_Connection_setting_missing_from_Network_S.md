---
title: "Wireless Connection setting missing from Network Settings"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by yclept on 2009-01-28
Hello all.  I'm running Hardy Heron 8.04 on a winPC and recently moved from a wired internet environment to a wireless environment, AKA my office out in the back yard, 150 ft from my cable modem.  

I recently bought a Belkin USB stick.  I have it working when I boot to Windows.  So, I have an internet connection on the same machine on which I am trying to get Ubuntu working.  I have a a laptop out here so I can troubleshoot while booted into linux.

OK, so here's the problem:

Network Settings doesn't give me an option for Wireless.  I see from the Help pages that there should be a third option besides the options I have. Wired Connection and Point to Point Connection options are there, just not Wireless Connection.

1.  How do I fix this problem?

1a. Can I update Ubuntu without a working network connection.  If not, I will haul the machine inside and get a wired connection.

Alternatively, I can download the newest version and reinstall.  The install should sense the usb stick, or at least install the missing pieces, I would think.

Any guidance/pointers/command suggestions are welcome.  I'm a long-time Ubuntu tinkerer who doesn't know unix ;-)  

Thanks in advance.

Shawn

---

### Post by yclept on 2009-01-28
Here are results from lsusb and lshw

:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 047d:101f Kensington PocketMouse Pro
Bus 001 Device 004: ID 045e:001d Microsoft Corp. Natural Keyboard Pro
Bus 001 Device 003: ID 050d:815c Belkin Components 
Bus 001 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 001 Device 001: ID 0000:0000 

lshw -C Network
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 11
       serial: 00:12:17:51:44:d8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes

---

### Post by dealcorn on 2009-04-21
I have the same issue in hardy.  After doing ndiswrapper stuff, System-Administration- Network reported no wireless interface.  Upon a fresh install with no update of any kind I verified that I see only Wired and Point to Point connections, no wireless.  My lsusb and lshw commands list similar output.

---


---
title: "Help with 2Wire router"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by SWSOE on 2009-12-17
I'm new to ubuntu and need some help setting it up to work with my 2Wire router. I use wired connection and a USB adapter.  Any help would be great.

---

### Post by bkratz on 2009-12-17
> **SWSOE said:**
> I'm new to ubuntu and need some help setting it up to work with my 2Wire router. I use wired connection and a USB adapter.  Any help would be great.

People will need a lot more information as to what you are trying to do-- or having problems with:

Perhaps this is a good starting point

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by SWSOE on 2009-12-17
Ill get more information if you want but I use a wired connection with a usb adapter.

---

### Post by Iowan on 2009-12-17
Start by posting **sudo lshw -C network** and **ifconfig -a** (both from terminal).

---

### Post by SWSOE on 2009-12-18
Got it:
 *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:a7:23:bd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:18:d7:df:fe:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes






eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a7:23:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27072 (27.0 KB)  TX bytes:27072 (27.0 KB)

pan0      Link encap:Ethernet  HWaddr 32:18:d7:df:fe:1c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by bkratz on 2009-12-18
I don't "see" the wireless USB dongle mentioned in the listing, was it plugged in when this was run?  You might post  "lsusb" 
also (LSUSB in lowercase no quotes).

---

### Post by SWSOE on 2009-12-18
Ok, Im going to explain my connection as easily as I can. There is a phone cord connected to a small device that has a usb cord that connects into my computer.  There is no wireless in all of this.

---

### Post by bkratz on 2009-12-18
> **SWSOE said:**
> Ok, Im going to explain my connection as easily as I can. There is a phone cord connected to a small device that has a usb cord that connects into my computer.  There is no wireless in all of this.

Finally, I think I understand. Well you should look at  lsusb anyway since it should show this device.

---

### Post by SWSOE on 2009-12-19
Here it is:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1630:0011  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c219 Logitech, Inc. Cordless RumblePad 2
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by SWSOE on 2009-12-21
Anyone have any ideas on whats wrong?

---

### Post by Iowan on 2009-12-21
> **SWSOE said:**
> Anyone have any ideas on whats wrong?Well... not really. I found several search results (for 82562EZ linux driver), but nothing really significant. Several threads were unresolved.  I don't remember dates - one thread suggested the e100 driver, [this]("http://www.mepis.org/docs/en/index.php/Intel_82562_or_82566_chipsets") one suggested the e1000 driver. I notice yours (and another Ubuntu thread I found) is 3.5.23-k4-NAPI (although module is e100).  I'm not experienced with drivers, so I'm not sure what the next step might be.

---


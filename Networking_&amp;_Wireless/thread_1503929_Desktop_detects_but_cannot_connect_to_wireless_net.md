---
title: "Desktop detects but cannot connect to wireless network"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by 12dan4 on 2010-06-07
I'm wondering here with my 64-bit 9.10 why my wireless does not seem to work with my Zonet wireless USB adapter. The adapter is working and it detects my network (a WPA) and attempts to connect, and after about 20 seconds or so, I am disconnected. Could someone please help? Even the tiniest bit of advice would help. Thanks.

---

### Post by Talon2 on 2010-06-07
What chipset set is in that wifi device?

```
lsusb
```

---

### Post by 12dan4 on 2011-04-17
Sorry for the near one year reply. I still haven't the problem fixed... so I give you this output for lsusb:

Bus 004 Device 002: ID 03f0:7904 Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by josephmills on 2011-04-17
hi there could we please see a ```
hwinfo --usb
``` thanks

---

### Post by 12dan4 on 2011-04-17
Hey.
Thanks for the reply, but unfortunately hwinfo is not installed, and I can't install it without uninstalling fglrx (an extremely weird problem), an unfavorable thing to do. It forces me to uninstall fglrx or else I can't do anything. So I could uninstall this for the moment and install hwinfo or... is there a way around this?
Sorry and thanks.

---

### Post by josephmills on 2011-04-17
> **12dan4 said:**
> Hey.
Thanks for the reply, but unfortunately hwinfo is not installed, and I can't install it without uninstalling fglrx (an extremely weird problem), an unfavorable thing to do. It forces me to uninstall fglrx or else I can't do anything. So I could uninstall this for the moment and install hwinfo or... is there a way around this?
Sorry and thanks.
no way to plug into a router?

---

### Post by 12dan4 on 2011-04-17
Yes I am plugged in the router currently to use the internet via ethernet. But I would still like to have wireless functionality as well.

---

### Post by josephmills on 2011-04-17
**with ** the machine plugged in please try ```
lsusb
``` 
**EDIT**: needs to repost lsusb last one is over a year old :)

---

### Post by 12dan4 on 2011-04-19
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by josephmills on 2011-04-19
hi there again could I please see a ```
lshw -C network
``` Thanks

---

### Post by 12dan4 on 2011-05-06
*-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 90:e6:ba:58:7a:42
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:29 memory:fe87c000-fe87cfff ioport:c880(size=8) memory:fe87e400-fe87e4ff memory:fe87e000-fe87e00f
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:b0:8c:09:b2:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless

---

### Post by 12dan4 on 2011-09-03
Bump.
I am using a zonet zew2545 and I have blacklisted rt2800usb

---

### Post by josephmills on 2011-09-03
hey there again lets see a ```
lsmod 
``` and see what mods are loaded

---


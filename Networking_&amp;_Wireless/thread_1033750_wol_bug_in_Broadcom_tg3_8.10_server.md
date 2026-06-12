---
title: "wol bug in Broadcom tg3 8.10 server"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by IQRules on 2009-01-07
Found this link, [http://patchwork.ozlabs.org/patch/12751/](http://patchwork.ozlabs.org/patch/12751/)

01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
02:0a.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)

I have this script,

#!/bin/sh 

wakeonlan -i 192.168.1.255 00:10:18:0a:40:2d

When the magic packet arrives, does the event get logged in the system?

I turned the wol feature by ethtool.

Any workaround, besides build my own kernel.

Thanks

---

### Post by dmizer on 2009-01-07
Not sure about a bug, but I got my WOL to work with the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

---

### Post by IQRules on 2009-01-08
Do you use tg3 driver in your machine?
Can you post lsmod | grep tg3 or lspci | grep -i ether?

---

### Post by dmizer on 2009-01-08
> **IQRules said:**
> Do you use tg3 driver in your machine?
Can you post lsmod | grep tg3 or lspci | grep -i ether?

I am not using the tg3 driver on any of my machines. I'm using an RTL-8169 gigabit card which uses the r8169 module. Just thought I would pass on my WOL experience, because I couldn't make mine work until I found the above thread.

---

### Post by IQRules on 2009-01-09
root@ubuntuHP:~# cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCI0	  S4	 disabled  no-bus: pci0000:00
XPA	  S4	 disabled  pci:0000:00:02.0
SLO4	  S4	 disabled  
XPB	  S4	 disabled  pci:0000:00:04.0
SLO2	  S4	 disabled  pci:0000:40:00.0
HUB	  S4	 disabled  pci:0000:00:1e.0
COM1	  S4	 disabled  pnp:00:08
USB1	  S3	 disabled  pci:0000:00:1d.0
USB2	  S3	 disabled  pci:0000:00:1d.1
USB3	  S3	 disabled  pci:0000:00:1d.2
USB4	  S3	 disabled  pci:0000:00:1d.3
EUSB	  S3	 disabled  pci:0000:00:1d.7
**[COLOR="Red"]NIC	  S4	 disabled  pci:0000:01:00.0[/COLOR]**
PBTN	  S4	*enabled   
root@ubuntuHP:~# ethtool -i eth0
driver: tg3
version: 3.94
firmware-version: 5751-v3.29a
bus-info: [COLOR="Red"]0000:01:00.0[/COLOR]

What is your setting?

---

### Post by dmizer on 2009-01-10
Here you go.
```
cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCI0	  S4	 disabled  no-bus:pci0000:00
HUB	  S4	 disabled  pci:0000:00:1e.0
COM1	  S4	 disabled  pnp:00:08
COM2	  S4	 disabled  pnp:00:09
USB1	  S3	 disabled  pci:0000:00:1d.0
USB2	  S3	 disabled  pci:0000:00:1d.1
USB3	  S3	 disabled  
EUSB	  S3	 disabled  pci:0000:00:1d.7
PBTN	  S4	*enabled   
```
```
ethtool -i eth1
driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:05:09.0
```

---

### Post by IQRules on 2009-01-10
How about this,

$ grep -i r8169 /etc/default/*

Just did this,
```


root@ubuntuHP:/# acpitool -W 13
  Changed status for wakeup device #13 (NIC	)

   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PCI0	  S4	 disabled  no-bus:pci0000:00
  2. XPA	  S4	 disabled  pci:0000:00:02.0
  3. SLO4	  S4	 disabled  
  4. XPB	  S4	 disabled  pci:0000:00:04.0
  5. SLO2	  S4	 disabled  pci:0000:40:00.0
  6. HUB	  S4	 disabled  pci:0000:00:1e.0
  7. COM1	  S4	 disabled  pnp:00:08
  8. USB1	  S3	 disabled  pci:0000:00:1d.0
  9. USB2	  S3	 disabled  pci:0000:00:1d.1
  10. USB3	  S3	 disabled  pci:0000:00:1d.2
  11. USB4	  S3	 disabled  pci:0000:00:1d.3
  12. EUSB	  S3	 disabled  pci:0000:00:1d.7
  13. NIC	  S4	 enabled   pci:0000:01:00.0
  14. PBTN	  S4	*enabled

```

---


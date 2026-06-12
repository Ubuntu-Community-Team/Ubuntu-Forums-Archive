---
title: "Dell Inspiron 8200: No wifi. Intel PRO 2915ABG"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by itlarson on 2013-06-23
I have an old DSell Inspiron 8200 with Xubuntu 12.04 installed.  Ethernet works fine, but there is no wifi.  I have switched to wicd, but there is no change.  Wicd says "no wireles networks found", even though it is sitting next to the router.  Here's some info on my setup:

               *-network:1
                description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:c3:8f:54
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
                resources: irq:11 memory:f8ffe000-f8ffefff

Looks like my driver should be "ipw2200" but "sudo lsmod | grep ipw" outputs precisly nothing.

Heres the output from "ifconfig"

eth0      Link encap:Ethernet  HWaddr 00:06:5b:bc:b2:32  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:febc:b232/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4066947 (4.0 MB)  TX bytes:576089 (576.0 KB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

And "iwconfig"

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

From "lspci" there is 

02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

But no mention of wireless.  
Any help would be apreciated.

---

### Post by praseodym on 2013-06-23
Please show the outputs of
```

lspci -nnk | grep -iA2 net
rfkill list
```
What about loading the driver by hand?
```

sudo modprobe -v ipw2200
```

---

### Post by itlarson on 2013-06-23
lspci only shows the 3com tornado ethernet adapter, and "rfkill list" outputs nothing.  modprobe installed ipw2200 and several other drivers sucessfully, but it has no effect.  Could this be a hardware issue?  I probably could get a new wireless adapter cheaply at my local FreeGeek.

---

### Post by praseodym on 2013-06-23
Tried to reset the BIOS to default?

---

### Post by itlarson on 2013-06-23
No efect.

---

### Post by praseodym on 2013-06-24
Obviously the card is not recognized, check:
```

cat /etc/udev/rules.d/70-persistent-net.rules
```
Checked the slot?

---

### Post by itlarson on 2013-06-24
That does show an eth1.  I'll shorten things since the internet is down and I'm typing this on my phone.  

PCI device --- (ipw2200)
Subsystem net
Action add
Drivers "?*"
Attr(address) ---
Attr(dev I'd) "0x0"
Attr(type) 1
Kernel "eth"
Name eth1

The dashes sub for lots of numbers and I didn't show the part for eth0

Also I removed the card and replugged it with no effect.

---

### Post by praseodym on 2013-06-24
Check in the BIOS if the card is "on". Maybe the boot priority needs to be 1st wireless and 2nd the OS.

Do you have a Live-CD/USB to check it there?

---

### Post by itlarson on 2013-06-24
The inspiron 8200 is too old to have boot from Ethernet- or USB for that matter.  Interestingly in the BIOS it shows the mini PCI device as enabled but unknown.  An inspiron 8600 I have shows it's PCI card as enabled and describes it as wireless.  They have almost the same BIOS.  

Sorry no live CD here, hopefully tonight.

---

### Post by Merrattic on 2013-06-24
Is there a physical switch ?

---

### Post by itlarson on 2013-06-24
Now were getting somewhere- the live cd connects just fine.  After booting back into my install, there is still no connection, but the adapter shows up in lspci and rfkill- which it didn't before.  Also lsmod shows ipw2200 as already installed, which it wasn't before.  I'm wondering if it was a bios setting that caused the initial problem, but I screwed someting up in the meantime.  I'll reinstall network manager and see if that fixes it- but it will have to be tomorrow.

---

### Post by itlarson on 2013-06-25
Yup, that fixed it.  I'd been messing around in the bios setting to get as much performance as possible, and that must be what caused the initial problem.  After resetting the bios, wicd wasn't getting the job done fore some reason.  Restoring network manager has got wifi working just fine.  Thanks a lot for all your help!

---


---
title: "Netgear n300"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by samishal on 2011-10-02
Hello,

I'm currently runnning Lubuntu and have had to buy a wireless adapater becuase my student accomodation does not have ethernet cables. The wireless adapter is a netgear n300 and it works great.. on windows but i cannot seem to get it to work on my linux system.

Does anyone know of a way to get the adapater to work in linux?

Sam

---

### Post by gandaran on 2011-10-02
first we need to know the wireless chipset model and brand
type in terminal and paste the output
```
lsusb
```
from the output we will check if you need to install driver or just do some minor fix.

---

### Post by samishal on 2011-10-02
> type in terminal and paste the output
Code:
lsusb

output of lsusb : 


```
sam@sam-Desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1bcf:05cf Sunplus Innovation Technology Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by samishal on 2011-10-02
???

---

### Post by gandaran on 2011-10-02
> Bus 001 Device 005: ID 0846:9020 NetGear, Inc
which version of Ubuntu do you have 10.04 or 11.04?
the device wasn't identified like I was expecting so I think you mite have 10.04.
using google search for the "ID 0846:9020" all I found was to use the windows XP driver with ndiswrapper, you can go this way with the windows XP driver but I still think if you can find out which chip the adapter has from windows (control panel » system » hardware tab) you can use linux drivers.
I think it could be Broadcom and if it is you can install the linux broadcom drivers from software package manager.

this is a guide on how to install the windows drivers
[http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520)

---

### Post by samishal on 2011-10-02
I'm curretnly using the Lubuntu distro on 11.04 after following your instructions (control panel » system » hardware tab) but i coudlnt find any information relating to the chip set

---

### Post by samishal on 2011-10-02
hi sorry i found the provider of teh drivers and its broadcom. can you please tell me how to install the broadcom drivers?

---

### Post by gandaran on 2011-10-02
> **samishal said:**
> hi sorry i found the provider of teh drivers and its broadcom. can you please tell me how to install the broadcom drivers?
there are many broadcom drivers, connect with wired internet and open synaptic package manager, click the refresh button then type in search box "bcm", the problem is that without the chipset model you don't know which one to install.

---

### Post by gandaran on 2011-10-02
> I'm curretnly using the Lubuntu distro on 11.04
check if **hwinfo** is installed, if it isn't install then run the **lsusb** command again

---

### Post by samishal on 2011-10-02
Hello ive, installed the broadcom common files, do i need to reboot the system? also, is there a way i can get the chipset information throguh linux?

---

### Post by samishal on 2011-10-02
> check if hwinfo is installed, if it isn't install then run the lsusb command again

this the output from lsusb after install of hwinfo : 

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1bcf:05cf Sunplus Innovation Technology Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

and this is the output from hwinfo i have selected on the netgear related portion of the code : 

```
53: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: X7GA.n6FVhxOY34D
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0
  SysFS BusID: 1-7:1.0
  Hardware Class: unknown
  Model: "NetGear Remote Download Wireless Adapter"
  Hotplug: USB
  Vendor: usb 0x0846 "NetGear, Inc."
  Device: usb 0x9020 "Remote Download Wireless Adapter"
  Revision: "0.01"
  Serial ID: "113"
  Speed: 480 Mbps
  Module Alias: "usb:v0846p9020d0001dcFFdsc00dp00icFFisc02ipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Hub)
```

---

### Post by Claus7 on 2011-10-02
Hello,

1) not think is a good idea to use usb instead of ethernet.
2) if you type lsusb and see the result for netgear (your output shows that is is recognised), then this does not mean that ubuntu has already the necessary drivers for the device already installed?

Sorry for the interruption.

Regards!

---

### Post by samishal on 2011-10-02
well obviously i would prefer to use the ethernet cable but i cannot at this time, also yes it would suggest that lubuntu has the correct drivers but i am still unable to see theavilable networks let only tell linux to scan for available networks

---

### Post by Claus7 on 2011-10-02
Hello,

this does not help you, yet I bought a cheap ethernet card to use with my ubu box. I had problems making it work under usb.

Good luck,
Regards!

---

### Post by samishal on 2011-10-02
no that did not help

---

### Post by samishal on 2011-10-03
Hello.

I've got a netgear n300 us wireless adapter. the adpater works fine for windows so its not a hardware fault but i cant get it to work for linux. when i do lsusb it shows up as netgear Inc. It's driver provider(fou this information throguh windows) is listed as broadcom but shows no other information. Can anyone help me?

Sam

---

### Post by samishal on 2011-10-03
Hello, 

I have a Netgear n300 Wireless usb adapter. I cannot seem to get it to work under Linux. However it does work under windows so must be a driver issue rather than hardware. I have found the the drivers are provided for windows by broadcom and that the model of this adapter is a WNA3100 Can anyone help me please?

Sam

---

### Post by mörgæs on 2011-10-03
I have merged your three threads on the same problem. Please don't open more of them.

---

### Post by westie457 on 2011-10-03
When using the dongle with Windows which driver is being used? Check via Control Panel > Device Manager > Network Adapters.

Thank you.

---


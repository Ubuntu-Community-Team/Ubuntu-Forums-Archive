---
title: "Activating Netgear A6200 wireless usb card on Ubuntu 12.10"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by derick881 on 2013-02-18
I am running a desktop computer with and Asus motherboard and AMD Phenom II  x 4 processor.  It is a 65 bit machine.  I installed Ubuntu 12.10 last week and am still trying to get the wireless usb adapter working.  I installed a driver for this device using the Windows Wireless Drivers App (ndisgtk).  The driver is bcmwlhigh63 which I got from the Netgear site.  ndisgtk reports that it is an appropriate driver and hardware is present.  
From the desktop I am not getting any signal on the top tray.  I am at a loss on where to proceed from here.

---

### Post by tester1957 on 2013-03-03
> **derick881 said:**
> I am running a desktop computer with and Asus motherboard and AMD Phenom II  x 4 processor.  It is a 65 bit machine.  I installed Ubuntu 12.10 last week and am still trying to get the wireless usb adapter working.  I installed a driver for this device using the Windows Wireless Drivers App (ndisgtk).  The driver is bcmwlhigh63 which I got from the Netgear site.  ndisgtk reports that it is an appropriate driver and hardware is present.  
From the desktop I am not getting any signal on the top tray.  I am at a loss on where to proceed from here.

the driver number you listed bcmwlhigh63 is not the driver that I got with the A6200 the correct driver is  bcmwlhigh5.inf is what you want to load in ndisgtk... having said that the A6200 does not perform well with the netgear driver

---

### Post by cdoebbler on 2013-05-09
To say that "the A6200 does not perform well with the netgear driver" is an understatement...A6200 does not work with any Ubuntu edition...Ubuntu/Cannonical/Netgear just have not supported it this USB WiFi stick (or any of the newest a/c wifi sets that I can see). Sad, but true. If I am wrong please correct me, but I have tried about fifty alleged work-arounds on about five different machines with no luck at all. It is merely a failure of support (and admittedly ability from people like me trying to hack solutions together) by the people at Ubuntu/Cannonical/Netgear.

---

### Post by cdoebbler on 2013-05-24
I think you are out of luck. Unless Ubuntu or Netgear provide a driver it just does not seem to work. It is a shame that even Ubuntu 13.10, which is still in development and which I tested does not seem to provide a solution. Neither the hardware manufacturer or the Ubuntu community seem to like the new a/c hardware...it surprises me as I thought that Ubuntu community would keep up to date with latest networking technology. Several university departments in Palestine and Sudan have Netgear A6200 modems and had to switch from Ubuntu back to Windows to use them.

---


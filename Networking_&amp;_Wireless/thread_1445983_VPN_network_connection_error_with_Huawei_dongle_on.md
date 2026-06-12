---
title: "VPN network connection error with Huawei dongle on sony viao laptop"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by prabashbala on 2010-04-03
HI ,I have a strange problem.I have installed Ubuntu 10.04 LTS (Lucid Lynx) Beta 1 on sony vaio vpceb1e0e laptop. My ubuntu installation detects my Huawei E1550 usb moddem/dongle and works fine.But the problem is,  
 
This doesn't work at this states. 
 
1) when I first boot in to ubuntu installation  
2) restart again with plugged dongle 
3) unplug and replug the usb Huawei dongle  
 
When it is not working ,what ever I have tried to make it work has been unsuccessful. 
 
Alternatively if i boot the machine in to windows 7 installation and reboot in to the ubuntu installation huawei connection starts working fine. 
 
If Huawei 3 connection is available it  shows  In the VPN connections section next to the date and time area of the upper control panel.This allow me to connect and disconnect options as well. 
 
In the not working state ,Even though it doesn't work ,If i run lsusb it gives this  
 
prabash@prabash-vaio:~$ lsusb 
Bus 002 Device 004: ID 1516:1213 CompUSA  
Bus 002 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd.  
Bus 002 Device 002: ID 8087:0020   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 0c45:6409 Microdia  
Bus 001 Device 002: ID 8087:0020   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
prabash@prabash-vaio:~$  
 
I can see that modem has been detected as "Bus 002 Device 003: ID 12d1:1446 Huawei Technologies Co., Ltd. " but ubuntu doesn't allow me a option to connect this dongle to the Internet. 

How can I connect the dongle to the Internet when it is in the not working state.
 
Thanks in advance for any ideas. 
 
Prabash

---

### Post by prabashbala on 2010-04-15
Several new USB devices (especially high-speed wireless WAN stuff, there seems to be a chipset from Qualcomm offering that feature) have their MS Windows drivers onboard; when plugged in for the first time they act like a flash storage and start installing the driver from there.
After that (and on every consecutive plugging) this driver switches the mode internally, the storage device vanishes (in most cases), and a new device (like a USB modem) shows up. 
I installed the [usb-modeswitch ]("http://packages.ubuntu.com/karmic/usb-modeswitch")and now my moddem working fine.I am very happy.

I would like to record my experience for some one  to save time.

This has solved my problem.
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by pdc on 2010-04-16
well done; good work; thanks for the feedback

the latest version of usb_modeswitch, the 1.1.1 seems to autoconfigure so the user should not need to edit any files: just install

---


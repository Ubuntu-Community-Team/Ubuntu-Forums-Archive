---
title: "Installing Option Velocity USB in Ubuntu Desktop 10,04"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by wlstiles3 on 2010-08-12
Can anyone help me install the Option Velocity 3G USB card?  I am using Ubuntu 10.04 Desktop.  I just installed the OS.  I love it.  But I cannot access the net on that machine without the USB card.

---

### Post by alexfish on 2010-08-12
hi
can you post the results of this code from the terminal

CODE:

lsusb -t

---

### Post by wlstiles3 on 2010-08-13
/:     Bus 03. Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/4p, 12M
/:    Bus 02. Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/4p, 12M
/:    Bus 01. Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
       l_ Port  3:  Dev 2, if 0,  Class=stor.,  Driver=usb-storage,  480M

---

### Post by alexfish on 2010-08-13
can you post the results of
please remove unnecessary usb devices before using this command

Code:

lsusb

this will hopefully give device id

---

### Post by wlstiles3 on 2010-08-13
Bus 003 Device 001:  ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001:  ID1d6b:0001  Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0af0:7a05 Option
Bus 001 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub

---

### Post by alexfish on 2010-08-13
hi

from the two device listings it shows the modem in an un-switched mode

so it is not recognised as a modem

I have looked through the device data base for switch-able devices (usb_modeswitch)
it is not listed in the current data

you can try this if usb_modeswitch is installed try removing it , but don't remove completely, then see what happens

or if not installed look here, they also have a forum , very helpful also if any devices show on the desktop try to eject the device

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

also the device is listing as an option devices

can,t be sure of what to do here , some recommend looking here, extract from modeswitch site

**All Option devices**
All known Option devices use the USB  storage command REZERO UNIT for switching (inherited from SCSI). Older  devices change vendor and product ID, newer ones don't (just their  device class). These newer sticks have a special interface after  switching (HSO) for which there is a specific driver. Some older devices  are able to be loaded with the new HSO firmware which changes their  behaviour.
Note: for HSO driver questions and HowTos consult the fine  [Pharscape]("http://www.pharscape.org/") site!

look at both sites , usb_modeswitch would be the first , josh may be able to advise further

regards

alexfish

---

### Post by wlstiles3 on 2010-08-14
Thanks for the help Alexfish.  I did find a lot of info at the websites  you suggested.  Unfortunately, I'm too clueless to install the drivers and work in  linux.  I need to learn more and then give this another try.  Thanks

---


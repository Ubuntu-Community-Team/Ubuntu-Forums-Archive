---
title: "Huawei ETS6630 - not recognized"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by czr.san on 2010-07-06
Hello Guys, 

I recently switched from windows to Ubuntu, like everyone else around here :). We are talking about one old laptop toshiba T8000, 128 RAM, one usb port, one modem, no ethernet :D cool!. using this only for browsing. 
Anyway I am trying to install the modem Huawei ETS6630 and I'm not sure how to set the device to be recognized as a modem, not as a storage device. Here is what I did:

**1**. I have installed the driver from here: [http://www.draisberghof.de/usb_modeswitch/#install](http://www.draisberghof.de/usb_modeswitch/#install)

**2**. from terminal: usb_modeswitch -v 12d1 -p 1011 -H
results:
marius@marius:~$ sudo usb_modeswitch -v 12d1 -p 1011 -H
[sudo] password for marius: 

Looking for default devices ...
Found devices in default mode or class (1)
Accessing device 002 on bus 001 ...
Using endpoints 0x04 (out) and 0x83 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
OK, driver found ("usb-storage")
OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Huawei, Incorporated
     Product: Huawei Technologies
  Serial No.: not provided
-------------------------
Sending Huawei control message ...
OK, Huawei control message sent
-> Run lsusb to note any changes. Bye.

**3**. After this the modem should have been present when trying to add a new mobile broadband device. But is not!

The modem is using the same port as other storage devices because is the only one. 

Any suggestions?

---

### Post by pdc on 2010-07-07
perhaps we just get you to join the usb_modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Josh is the expert there; runs the programme and moderates the forum: very helpful guy;

he should get you up and running in no time

---

### Post by philinux on 2010-07-07
```
sudo apt-get install usb-modeswitch
```

See the General Help forum sticky thread for more info.

---

### Post by pdc on 2010-07-08
I am sure this will be very helpful Phil

Josh at the usb_modeswitch webpage

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

recommends installing the latest version 1.1.3-1 which he says (as a .deb package) is only available at the Debian repository (sid unstable)

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

I suspect the Ubuntu may not be as up to date?

I find that Josh on the usb_modeswitch forum can help folks where things ain't panning  out correctly for them .......

---


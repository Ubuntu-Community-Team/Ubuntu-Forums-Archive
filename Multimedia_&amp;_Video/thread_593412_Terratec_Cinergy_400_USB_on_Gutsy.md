---
title: "Terratec Cinergy 400 USB on Gutsy"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by termostaat on 2007-10-27
Hello,

there has been a previous question about the Terratec Cinery 400 USB but without a resolution so let me repost.

Configuration: Dell D830 - Terratec Cinergy 400 USB (Ubuntu 7.10 - regular distribution kernel)

root@D830:~# lsusb
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0ccd:003b TerraTec Electronic GmbH 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:8140 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  

root@D830:~# hwinfo --usb
11: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_ccd_3b_ViP5000_if0
  Unique ID: +u4I.k38V8oneaM1
  Parent ID: 7eqy.vfMN5defVA1
  SysFS ID: /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0
  SysFS BusID: 6-2:1.0
  Hardware Class: unknown
  Model: "TerraTec Cinergy 400"
  Hotplug: USB
  Vendor: usb 0x0ccd "TerraTec"
  Device: usb 0x003b "Cinergy 400"
  Revision: "1.00"
  Serial ID: "ViP5000"
  Speed: 12 Mbps
  Module Alias: "usb:v0CCDp003Bd0100dc00dsc00dp00icFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Hub)

When walking through the "card=" numbers while modprobe'ing, the tvtime response remains: videoinput: Cannot open capture device /dev/video0: No such file or directory

I hardcoded the module alias into /etc/modprobe.d/aliases but to no avail so it seems that the TV tuner is not detected by the kernel at all. I am wondering whether this is an USB issue rather than a driver issue but have no idea actually:

So, if anybody has some experience with  this or has additional ideas, I would be very thankful,

T.

---

### Post by benpeti on 2008-02-09
Hi!

Did you get any reply?
Does anybody know how to get this device work with Ubuntu 7.10? I've read a lot how-to about Cinergy 250 USB and Cinergy 400 Mobile (PCMCIA interface), but no info about Cinergy 400 USB.

Thanks,
Peter

---

### Post by lubosz on 2008-03-16
same here....
i have a TerraTec Electronic GmbH Cinergy T^2 DVB-T Receiver, but the kernel module is not added. so there is no /dev/video1 device i can open with tvtime (argument --device=DEVICE)
video0 is my webcam ;)
any kernel extensions for cinergy cards?

---

### Post by lubosz on 2008-03-16
this worked for me:
[http://doc.ubuntu-fr.org/terratec_cinergy_t2](http://doc.ubuntu-fr.org/terratec_cinergy_t2)

(its in french, but you just have to install some stuff and run kaffeine)

---


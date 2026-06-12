---
title: "Need help with an older model ibm webcam"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by alnhntr29 on 2008-01-18
I have an older model IBM webcam, I would like to know if anyone knows how to get this thing to work. Kubuntu 7.10, Xubuntu 7.10. It is being detected and I have tried almost every  
camera program I could find, but to no avail. Is there any other driver for any other model that will work?

---

### Post by linuxwizard on 2008-01-18
Post results of command  > lsusb

---

### Post by tgalati4 on 2008-01-18
If it's an IBM netcamera (PC Camera P/N 33L4889) it works under Linux Mint 4 XFCE (gutsy) using xawtv using the hal-detected driver.  

lsusb looks like:

Bus 003 Device 002: ID 0545:8002 Xirlink, Inc. IBM NetCamera

lsmod looks like:

uhci_hcd               26640  0 
usbcore               138632  9 ibmcam,usbvideo,xpad,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

I put ibmcam at the bottom of /etc/modules to force load it even when not connected.

There are some IBM netcams that compress the image and the current drivers don't know how to handle the data stream.  You could have one of those.

---


---
title: "Quickcam express"
date: 2009-04-13
forum: Multimedia Software
---

### Post by hvc123 on 2009-04-13
Hey all,

iwonder if anyone can elp?

i have a quickcam express hooked up to my intrepid ppc box but im unable to connect to the camera. 
i have used the qsca and quickcam drivers but i cant get the /dev/video/ to be created....

here is my dmesg of the quickcam
[  990.916821] usb 3-2: new full speed USB device using ohci_hcd and address 8
[  991.126099] usb 3-2: configuration #1 chosen from 1 choice

thats all i get 2 lines for this device.
when i modprobe the qsca driver it does not create the /dev/video dirs. 
if i do lsusb i get 

Bus 003 Device 008: ID 046d:0840 Logitech, Inc. QuickCam Express

so it knows what it is but does not create teh /dev/video
has anyelse found  this or a solution.. 

thanks

---

### Post by hvc123 on 2009-04-14
bump! ?

---


---
title: "[Knoppix] - Trying to mount HP Photosmart M415 to retrieve pics"
date: 2009-10-02
forum: Multimedia Software
---

### Post by DnDer on 2009-10-02
I do not have a card reader, so I have to plug in the USB adapter. The camera just hangs on "establishing connection. I thought maybe I just have to mount it to get it done right, so I "sudo mount /dev/sdb1 /mnt" (sda1 is my hard drive with windows, which doesn't want to download the pictures on it right) which should have mounted the camera after I turned it on. I'm told "mount: special device /dev/sdb1 does not exist."

A quick googling found me the line "dmesg | grep usb" to run for getting drivers and getting it to work. (I have no idea what it does... But I'm on a live distro, what could it hurt?) 

Here's the output relevant to the camera, I think:
```
[    5.459975] usb 1-2.3.4: New USB device found, idVendor=06f2, idProduct=0011
[    5.459979] usb 1-2.3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.459982] usb 1-2.3.4: Product: 2
[    5.459985] usb 1-2.3.4: Manufacturer: 1
[    5.459987] usb 1-2.3.4: SerialNumber: 3
[    9.312959] usb-storage: device scan complete
[  203.553076] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  203.895887] usb 4-1: configuration #1 chosen from 1 choice
[  203.899055] usb 4-1: New USB device found, idVendor=03f0, idProduct=7a02
[  203.899060] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  203.899063] usb 4-1: Product: HP PhotoSmart M415 Camera
[  203.899066] usb 4-1: Manufacturer: HEWLETT-PACKARD 
[  406.722850] usb 4-1: USB disconnect, address 2
[  422.948681] usb 1-4: USB disconnect, address 3
[  436.277110] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  436.620842] usb 4-2: configuration #1 chosen from 1 choice
[  436.624053] usb 4-2: New USB device found, idVendor=03f0, idProduct=7a02
[  436.624057] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  436.624061] usb 4-2: Product: HP PhotoSmart M415 Camera
[  436.624064] usb 4-2: Manufacturer: HEWLETT-PACKARD 
knoppix@Microknoppix:~$ 
```

And all of that means nothing to me in context... Is the information required to mount the camera somewhere in there?

---


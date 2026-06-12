---
title: "USB Bluetooth Dongle doesn't work"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by ecolitan on 2009-03-04
I have a Bluetooth dongle which I cant get to show up so I can use.

The information I have for the device is:

```
aaron@hector:~$ lsusb
Bus 003 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

aaron@hector:~$ lsmod
Module                  Size  Used by
btusb                  19736  3 
usbcore               149360  5 btusb,usbhid,uhci_hcd,ehci_hcd
bluetooth              61924  19 btusb,sco,bnep,rfcomm,l2cap

aaron@hector:~$ dmesg
[17733.410361] btusb_intr_complete: hci0 urb dc804180 failed to resubmit (19)
[17733.416880] btusb_send_frame: hci0 urb d7deeb80 submission failed
[17752.724042] usb 3-1: new full speed USB device using uhci_hcd and address 6
[17752.923081] usb 3-1: configuration #1 chosen from 1 choice
```

I hunted around and saw that some people were complaining about the btusb driver, which superseeded the hci_usb driver which was claimed to work with this dongle. Is there anyway I can try the hci_usb driver? It doesn't just install with modprobe?

```
aaron@hector:~$ modprobe hci_usb
FATAL: Module hci_usb not found.
```

Edit: just also looked up at [http://linuxlaptopwiki.net](http://linuxlaptopwiki.net) that hci_usb is a working driver for this device, so i prolly just need to get this driver in.

Any ideas???

---

### Post by aletum on 2010-02-11
In order to get hci_usb driver on post-2.6.28 kernel systems which switched to btusb, you have to
- obtain kernel source version when hci_usb was still used (2.6.27 or earlier) 
- get /drivers/bluetooth/hci_usb.c and hci_usb.h
- copy them into your current kernel's sources folder /drivers/bluetooth
- modify that folder's Makefile: put on top obj-m += hci_usb.c
- then from the source's main folder run make $SUBDIRS=/drivers/bluetooth modules
- you might get some compilation errors. If so, note the problematic lines and edit/erase/comment out the problematic lines of code.
- then there should be a hci_usb.ko file - which is just what's needed
Although I'm not sure how to load it with modprobe, cause modprobe only loads certain modules which are stated in some config file.
Well, there's homework for you!!!
Keep in mind that you may need to downgrade your bluez package to the version which was around 2.6.27 times. Also watch out for rfkill blocking your device. (rfkill list to check)
Good luck.

---


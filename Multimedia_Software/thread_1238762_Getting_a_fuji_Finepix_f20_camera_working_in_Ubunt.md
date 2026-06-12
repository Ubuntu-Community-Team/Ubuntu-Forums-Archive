---
title: "Getting a fuji Finepix f20 camera working in Ubuntu"
date: 2009-08-12
forum: Multimedia Software
---

### Post by slothario on 2009-08-12
Hi all,

I tried getting my camera to work in ubuntu, and I started by following [this thread's]("http://ubuntuforums.org/showthread.php?t=327613") directions, which basically involves editing /etc/udev/rules.d/45-libgphoto2.rules, but that didn't seem to do it. I opened digiKam and entered the model number and everything and tried to get it to recognize my camera, but to no avail.

Here's some revelevant command output that my linux geek friend told me to do:
```
[SIZE=3]lsusb | grep Fuji
Bus 005 Device 004: ID 04cb:ff80 Fuji Photo Film Co., Ltd [/SIZE]
```I ran udevadm then turned on my camera:
```
sudo udevadm monitor
udevmonitor will print the received events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UEVENT[1250119011.857895] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6 (usb)
UEVENT[1250119011.858632] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0 (usb)
UEVENT[1250119011.859036] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/usb_endpoint/usbdev5.8_ep01 (usb_endpoint)
UEVENT[1250119011.859305] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/usb_endpoint/usbdev5.8_ep82 (usb_endpoint)
UEVENT[1250119011.859584] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0/usb_endpoint/usbdev5.8_ep83 (usb_endpoint)
UEVENT[1250119011.859911] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/usb_endpoint/usbdev5.8_ep00 (usb_endpoint)
UDEV  [1250119011.864742] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6 (usb)
UDEV  [1250119012.014677] add      /devices/pci0000:00/0000:00:1d.7/usb5/5-6/5-6:1.0 (usb)
```relevant dmesg output:
```
[173160.916127] usb 5-6: new high speed USB device using ehci_hcd and address 7
[173161.050381] usb 5-6: configuration #1 chosen from 1 choice
```Any thoughts?

Danny

---

### Post by x22 on 2009-08-17
welcome to the forum

if by "work" you mean, make available to the OS its 
ram storage as "mini-hard drive," for reading/writing--
then once the camera is plugged in and turned on try

"ls /dev/sd* |grep floppy

to see whether it shows as "sda1" or "sdb1" etc--suppose
the first--then

"mount /dev/sda1 /mnt"

should make it available

---


---
title: "Connecting thermal camera using Windows driver and ndiswrapper"
date: 2012-06-22
forum: Multimedia Software
---

### Post by mmattb on 2012-06-22
I have a Guide M8 thermal imaging camera we are trying to hook up in our lab.  It has no Linux driver that I can find.  However, it does have a Windows driver.  I installed it using ndiswrapper, and the device is successfully recognized:


ndiswrapper -l

guideusb64 : driver installed
	device (0088:0067) present

It shows up under lsusb at that address, but has no driver listed or anything else distinctive.  Does anybody have a sense for how to access it at this point as a video stream?  Or to otherwise go about finding the ways I can interface with it?  

Note: under windows it does have a live USB mode like a webcam, and it has some Flash memory and other things of that nature.

I don't work much with hardware like this, so I am quite ignorant about how to do this.

My system: Ubuntu 12.04
Latest version of ndiswrapper from ubuntu repository and Windows driver from manufacturer.

---

### Post by mmattb on 2012-06-22
Update:

dmesg indicates possible problems with ndiswrapper (maybe not the way to go?):

```
[ 3672.983069] usb 1-1.2: new high-speed USB device number 68 using ehci_hcd
[ 3673.155053] usb 1-1.2: reset high-speed USB device number 68 using ehci_hcd
[ 3673.250931] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExAllocatePool'
[ 3673.250999] ndiswrapper (load_sys_files:199): couldn't prepare driver 'guideusb64'
[ 3673.251044] ndiswrapper (load_wrap_driver:121): couldn't load driver 'guideusb64'
[ 3836.602557] usb 1-1.2: USB disconnect, device number 68
[ 3840.138314] usb 1-1.2: new high-speed USB device number 69 using ehci_hcd
[ 3840.314330] usb 1-1.2: reset high-speed USB device number 69 using ehci_hcd
[ 3840.410330] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExAllocatePool'
[ 3840.410399] ndiswrapper (load_sys_files:199): couldn't prepare driver 'guideusb64'
[ 3840.410482] ndiswrapper (load_wrap_driver:121): couldn't load driver 'guideusb64'
[ 3842.489876] usb 1-1.2: USB disconnect, device number 69

```

---


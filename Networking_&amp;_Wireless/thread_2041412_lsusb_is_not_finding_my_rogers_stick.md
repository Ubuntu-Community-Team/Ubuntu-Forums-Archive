---
title: "lsusb is not finding my rogers stick"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by bleutyler on 2012-08-12
Hello everyone, 

I have read over a number of 'rogers stick' forums on this great community space.  As I try to get it setup, I seem to be stuck on the first step of all places.

I am running Ubuntu 12.04, a Dell Inspiron 1710 model.  The Rogers stick model is a ZTE MF668

This is the output of lsusb, with the device connected via USB.  The device has lights on it, and the light goes from red to blue when I plug it in.  This lsusb output is the same with the ZTE plugged in or not.



```

tyler@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 004: ID 0c45:6400 Microdia 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 003 Device 005: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth


```

---

### Post by papibe on 2012-08-12
Hi bleutyler.

I've seen some problems related to 
```
Bus 007 Device 006: ID 046d:c52b **[COLOR="Red"]Logitech, Inc. Unifying Receiver[/COLOR]**
```

Check this [thread]("http://ubuntuforums.org/showthread.php?t=1984294&highlight=Logitech"), and this [question]("http://askubuntu.com/questions/113984/is-logitechs-unifying-receiver-supported").

I would try to check if the stick is recognized removing other external USB devices (mouse, keyboard for instance). Then I would try the recommended solution to pair the other devices with the Unifying Receiver.

Regards.

---

### Post by bleutyler on 2012-08-12
Thank you for the suggestions.

I tried the unifiying script you recommended, and I get to the point where it asks to turn on the device.  I plug it in, but still no avail.

I have noticed that dmesg output seems to indicate the rogers stick isn't playing nice.  I have had all 3 USB devices busy with a mouse, keyboard and removable drive, and they all worked simultaneously.  

I wonder if the device is working properly, because the light on it is blue which means it _should_ be working, but Ubuntu just does not know to pass traffice through it.

This is the dmesg output I mentioned.

```


[ 9804.064049] usb 7-1: new full-speed USB device number 13 using uhci_hcd
[ 9804.188065] usb 7-1: device descriptor read/64, error -71
[ 9804.412165] usb 7-1: device descriptor read/64, error -71
[ 9804.628165] usb 7-1: new full-speed USB device number 14 using uhci_hcd
[ 9804.748118] usb 7-1: device descriptor read/64, error -71
[ 9804.972164] usb 7-1: device descriptor read/64, error -71
[ 9805.188083] usb 7-1: new full-speed USB device number 15 using uhci_hcd
[ 9805.596168] usb 7-1: device not accepting address 15, error -71
[ 9805.708062] usb 7-1: new full-speed USB device number 16 using uhci_hcd
[ 9806.120155] usb 7-1: device not accepting address 16, error -71
[ 9806.120188] hub 7-0:1.0: unable to enumerate USB device on port 1
[ 9873.940068] usb 7-1: new full-speed USB device number 17 using uhci_hcd
[ 9874.060176] usb 7-1: device descriptor read/64, error -71
[ 9874.284179] usb 7-1: device descriptor read/64, error -71
[ 9874.500115] usb 7-1: new full-speed USB device number 18 using uhci_hcd
[ 9874.620192] usb 7-1: device descriptor read/64, error -71
[ 9874.844070] usb 7-1: device descriptor read/64, error -71
[ 9875.060184] usb 7-1: new full-speed USB device number 19 using uhci_hcd
[ 9875.476158] usb 7-1: device not accepting address 19, error -71
[ 9875.644089] usb 7-1: new full-speed USB device number 20 using uhci_hcd
[ 9876.060076] usb 7-1: device not accepting address 20, error -71
[ 9876.060106] hub 7-0:1.0: unable to enumerate USB device on port 1


```

I plug in the keyboard right after, and dmesg now says:

```

[10742.760166] usb 6-2: new full-speed USB device number 18 using uhci_hcd
[10742.960745] input: Dell Dell Smart Card Reader Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input21
[10742.960940] generic-usb 0003:413C:2101.001E: input,hidraw3: USB HID v1.11 Keyboard [Dell Dell Smart Card Reader Keyboard] on usb-0000:00:1d.0-2/input0

```

---

### Post by bleutyler on 2012-08-12
I just tried to get teh stick to work on my wife's windows laptop, and it does not work their either.

I have spoken with technical support, and the device appears to be defective.  

Thanks everyone for your help.

---


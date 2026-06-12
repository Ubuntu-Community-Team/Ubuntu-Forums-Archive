---
title: "Enable USB mobile broadband in Jaunty"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by crompie on 2009-07-08
I use a USB mobile broadband modem (Huawei E220, or Nokia E51 phone, depending on signal availability from two service providers) on my Compaq notebook. Both these modems work well with minimal setup.

Problem is, I find that if I boot the system first, and then plug a modem in, it does not appear in the Network Manager applet list of available Mobile Broadband connections. The only way I can "enable" the connection is to make sure the USB modem is plugged in BEFORE booting. Then it works fine.

Incidentally, this behaviour only started since upgrading to Jaunty. On Intrepid, I could plug in a modem after booting, and it would appear in NM after a few seconds and I could connect.

Does anyone know how to get Network Manager to recognise a USB modem after it's plugged in with the notebook already booted?

Thanks for any suggestions.

---

### Post by GeorgeVita on 2009-07-12
Hi ****, just an idea to 'restart' udev and recognise again all peripherals?
```
sudo /etc/init.d/udev restart
```

or try a 'restart' of network-manager?
```
sudo /etc/init.d/NetworkManager restart
```

Regards,
George

---

### Post by crompie on 2009-08-24
Hi George

Sorry for my very late response...  :(

Thank you for your suggestion. I tried restarting both udev and network manager, but with no luck - the USB modem still does not appear in the list of available connections.

Any other ideas? Anyone...?

Thanks,
Mark

---

### Post by GeorgeVita on 2009-08-24
Hi Mark, do some checks 10-15 seconds after attaching modem and later phone to see system activity regarding usb ports and tty: ```
dmesg | grep -i usb
lsusb
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
```
Regards,
George

---

### Post by crompie on 2009-09-29
Hi George, my apologies again, I have not checked the forum for a long time...

I followed your suggestions, and here are the results from the terminal commands:

1) Here the modem was plugged in AFTER the system had booted (at this stage the modem does NOT appear in the list of available connections):

mark@mark-laptop:~$ dmesg | grep -i usb
[    0.583532] usbcore: registered new interface driver usbfs
[    0.583559] usbcore: registered new interface driver hub
[    0.583604] usbcore: registered new device driver usb
[    2.395556] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.395577] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.396148] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.454134] usb usb1: configuration #1 chosen from 1 choice
[    2.454173] hub 1-0:1.0: USB hub found
[    2.454334] uhci_hcd: USB Universal Host Controller Interface driver
[  152.884136] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  153.159428] usb 1-1: configuration #1 chosen from 1 choice
[  153.437670] Initializing USB Mass Storage driver...
[  153.448913] usb-storage: probe of 1-1:1.0 failed with error -5
[  153.449415] usb-storage: probe of 1-1:1.1 failed with error -5
[  153.449514] usbcore: registered new interface driver usb-storage
[  153.449529] USB Mass Storage support registered.
[  153.558648] usbcore: registered new interface driver usbserial
[  153.558708] USB Serial support registered for generic
[  153.558817] usbcore: registered new interface driver usbserial_generic
[  153.558828] usbserial: USB Serial Driver core
[  153.619610] USB Serial support registered for GSM modem (1-port)
[  153.621457] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  153.621692] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  153.621740] usbcore: registered new interface driver option
[  153.621750] option: v0.7.2:USB Driver for GSM modems

mark@mark-laptop:~$ lsusb
Bus 001 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mark@mark-laptop:~$ ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: cannot access /dev/ttyA*: No such file or directory
ls: cannot access /dev/ttyH*: No such file or directory
/dev/ttyUSB0  /dev/ttyUSB1

mark@mark-laptop:~$ 


2) Just for comparison, I also booted the system with the modem already plugged in, and repeated the commands. At this stage the option "Vodafone" does appear in the list of available connections, under Mobile Broadband. Here are the replies:

mark@mark-laptop:~$ dmesg | grep -i usb
[    0.583176] usbcore: registered new interface driver usbfs
[    0.583203] usbcore: registered new interface driver hub
[    0.583248] usbcore: registered new device driver usb
[    2.395691] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.395712] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.396283] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.454132] usb usb1: configuration #1 chosen from 1 choice
[    2.454170] hub 1-0:1.0: USB hub found
[    2.454331] uhci_hcd: USB Universal Host Controller Interface driver
[    2.820070] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    3.049172] usb 1-1: configuration #1 chosen from 1 choice
[    4.396983] Initializing USB Mass Storage driver...
[    4.403072] usb-storage: probe of 1-1:1.0 failed with error -5
[    4.403188] usb-storage: probe of 1-1:1.1 failed with error -5
[    4.403240] usbcore: registered new interface driver usb-storage
[    4.403247] USB Mass Storage support registered.
[   12.356548] usbcore: registered new interface driver usbserial
[   12.356610] USB Serial support registered for generic
[   12.356689] usbcore: registered new interface driver usbserial_generic
[   12.356693] usbserial: USB Serial Driver core
[   12.433596] USB Serial support registered for GSM modem (1-port)
[   12.433923] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   12.434072] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   12.434093] usbcore: registered new interface driver option
[   12.434098] option: v0.7.2:USB Driver for GSM modems

mark@mark-laptop:~$ lsusb
Bus 001 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mark@mark-laptop:~$ ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: cannot access /dev/ttyA*: No such file or directory
ls: cannot access /dev/ttyH*: No such file or directory
/dev/ttyUSB0  /dev/ttyUSB1

mark@mark-laptop:~$ 

I hope this helps!

Thank you.

---

### Post by GeorgeVita on 2009-09-30
> **crompie said:**
> [    4.403247] USB Mass Storage support registered.
[   12.356548] usbcore: registered new interface driver usbserial
[   12.356610] USB Serial support registered for generic
[   12.356689] usbcore: registered new interface driver usbserial_generic
[   12.356693] usbserial: USB Serial Driver core
[   12.433596] USB Serial support registered for GSM modem (1-port)
[B][   12.433923] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   12.434072] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   12.434093] usbcore: registered new interface driver option
[   12.434098] option: v0.7.2:USB Driver for GSM modems
[/B]
mark@mark-laptop:~$ lsusb
Bus 001 Device 002: ID **12d1:1003** Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

mark@mark-laptop:~$ ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
ls: cannot access /dev/ttyA*: No such file or directory
ls: cannot access /dev/ttyH*: No such file or directory
**/dev/ttyUSB0  /dev/ttyUSB1**


In both cases (boot with/without) it seems to be there!
Try to 'setup' manually a Mobile Broadband connection and test it.
Other options: **wvdial** (follow link from my signature) OR **wait 29 days for Ubuntu 9.10**

Regards,
George

---

### Post by crompie on 2009-10-04
Many thanks for your suggestions, George. I also saw that the USB modem is recognised and is present, but for some reason is just doesn't appear in the "available connections" list of Network Manager. Strange...

As this is not really a major problem for me, I think I'll wait for the next release of Ubuntu and see if the behaviour changes. After all, it used to work in version 8.10.

Regards,
Mark

---


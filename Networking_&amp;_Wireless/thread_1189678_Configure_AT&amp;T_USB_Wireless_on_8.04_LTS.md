---
title: "Configure AT&amp;T USB Wireless on 8.04 LTS"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by Lupgaru on 2009-06-17
I have a AT&T USB GSM Account and it's there in 8.10 and 9.04. Works great. I have 8.04 LTS on a desktop and all it will see is my linksys USB Wireless. 
    How do I get 8.04 to see this network? It's GSM, carrier is Cingular.:D

---

### Post by GeorgeVita on 2009-06-17
Hi **Lupgaru**,

usually a GSM account is used to connect to a GSM data network via GPRS/3G modem or phone.

Can you determine what kind of hardware (3G modem) do you have (manufacturer, model)?

Regards,
George

---

### Post by Lupgaru on 2009-06-17
> **GeorgeVita said:**
> Hi **Lupgaru**,

usually a GSM account is used to connect to a GSM data network via GPRS/3G modem or phone.

Can you determine what kind of hardware (3G modem) do you have (manufacturer, model)?

Regards,
George

Thank You George, this is what I found:
AT&T USB Connect Mercury
3G Broadband Connect Network
Global Coverage   1MB - 15 seconds
Specifications:
HSPA (850/1900/2100 MHz)
GPRS/EDGE (850/900/1800/1900 MHz)

Connection Information in Ubuntu 9.04 shows:
AT&T (default)
Interface   GSM (ttyUSB3)
Hardware Address:
Driver  sierra
Speed  unknown
Security  unknown

I hope you get the Attachment. 

This is all I know for now. Thanks for your help!

---

### Post by GeorgeVita on 2009-06-18
Hi again,
9.04 has a newer version of Network Manager (0.7.x) which recognises your modem.
On 8.04 it is possible to use another methode to connect (as wvdial or gnome-ppp).
We need some basic tests to see system activity.

Boot 8.04 PC without the modem, wait for the system to load, attach the modem, from a terminal window try: ```
lsusb
``` 
then ```
ls /dev/ttyU*
```

Copy data related to your modem an post them here. If no port found try: ```
dmesg
```
Copy here _only the last 10-15 lines_ regarding the modem, serial driver.

Regards,
George

---

### Post by Lupgaru on 2009-06-18
> **GeorgeVita said:**
> Hi again,
9.04 has a newer version of Network Manager (0.7.x) which recognises your modem.
On 8.04 it is possible to use another methode to connect (as wvdial or gnome-ppp).
We need some basic tests to see system activity.

Boot 8.04 PC without the modem, wait for the system to load, attach the modem, from a terminal window try: ```
lsusb
``` 
then ```
ls /dev/ttyU*
```

Copy data related to your modem an post them here. If no port found try: ```
dmesg
```
Copy here _only the last 10-15 lines_ regarding the modem, serial driver.

Regards,
George

Here's what I got after the first 2 Codes:
stephen@stephen-desktop:~$ lsusb 
Bus 004 Device 004: ID 1199:6880 Sierra Wireless, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical 
Bus 001 Device 001: ID 0000:0000  
stephen@stephen-desktop:~$ ls/devttyU* 
bash: ls/devttyU*: No such file or directory 

Here's the last lines after Code: dmesg
[  151.609055] usb 4-5: USB disconnect, address 3 
[  151.609485] sierra: probe of 4-5:1.0 failed with error -5 
[  151.878476] usb 4-5: new high speed USB device using ehci_hcd and address 4 
[  152.023479] usb 4-5: configuration #1 chosen from 1 choice 
[  152.067973] usbcore: registered new interface driver sierra 
[  152.067983] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b 
[  152.089216] usbcore: registered new interface driver libusual 
[  152.138099] Initializing USB Mass Storage driver... 
[  152.149939] scsi2 : SCSI emulation for USB Mass Storage devices 
[  152.153172] usbcore: registered new interface driver usb-storage 
[  152.153185] USB Mass Storage support registered. 
[  152.154154] usb-storage: device found at 4 
[  152.154162] usb-storage: waiting for device to settle before scanning 
[  157.151598] usb-storage: device scan complete 
[  157.153778] scsi 2:0:0:0: Direct-Access     SWI      SD Card          2.31 PQ: 0 ANSI: 2 
[  157.163696] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
[  157.163805] sd 2:0:0:0: Attached scsi generic sg2 type 0 

Hope this helps, it seems that after the first Code it recognized the Modem but nothing happened.
    I'm new at this Modem stuff, hope you know what I need to do.
Thanks ever so much.
Stephen:)

---

### Post by GeorgeVita on 2009-06-19
Hi again,
from the output your modem shown as "Sierra Wireless USB modem" with identification 1199:6880
As we do not have the same hardware there is always a possibility for our efforts to fail,
... but we must try!

> stephen@stephen-desktop:~$ **ls/devttyU***
bash: ls/devttyU*: No such file or directory 

you mistyped the command, try once more:

```
**ls /dev/ttyU***
```

If it shows NO port created, try:
```
sudo modprobe usbserial vendor=0x1199 product=0x6880
```
and retry the ls /dev/ttyU* command.

Notes: **lsusb** lists all USB peripherals attached to your PC. Each peripheral has a unique identification (your modem has vendorID=0x1199 and productID=0x6880). **dmesg** shows all system activity. **ls /dev/ttyU*** will list all serial communications port created (or existed). One of them will be the usable for your modem. Finally **modprobe usbserial** will try to "force" the system creating the communication ports.

 **[COLOR="Red"]>>>[/COLOR] I found a thread more specific to your modem: [http://ubuntuforums.org/showthread.php?t=946379](http://ubuntuforums.org/showthread.php?t=946379)**


Regards,
George

---

### Post by Lupgaru on 2009-06-21
Hi George
Well it still didn't work but the thread you sent did, Thanks Ever so Much for your Help!

---


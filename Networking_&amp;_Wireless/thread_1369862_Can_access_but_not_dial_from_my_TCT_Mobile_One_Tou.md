---
title: "Can access but not dial from my TCT Mobile One Touch X200S 3G USM Modem"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by DavidHOB on 2010-01-01
Hello,

I'm not experienced at Ubuntu but have been searching the forums for 2 days to fix this and feel very close...I hope someone can provide the key to solve this. I cannot get my 3G modem to work using wvdial...

[U][B]Summary:
[/B][/U]
My X200S 3G USB modem is initially seen as a storage device, so I have pieced the following process together which works until the last command (wvdial) which "cannot get information for serial port" and states "modem not responding":

[INDENT]sudo usb_modeswitch
[/INDENT][INDENT]sudo mount -t usbfs usbdevfs /proc/bus/usb
[/INDENT][INDENT]sudo cat /proc/bus/usb/devices
[/INDENT][INDENT]sudo modprobe usbserial vendor=0x1bbb product=0xf000
[/INDENT][INDENT]sudo dmesg
[/INDENT][INDENT]sudo wvdial virgin
[/INDENT]
[U][B]System Information:
[/B][/U]
PC:             Dell Inspiron Mini S Laptop
3G Card:     TCT Mobile One Touch X200S
OS:             Dell Ubuntu Hardy 8.04 (I do not wish to upgrade or change this)
                  Network Manager Version 0.7.0


[U][B]Detail:
[/B][/U]
-     Network Manager does not auto-config Mobile Broadband, and manual config makes no difference so currently I have removed all Mobile Broadband connections from Network Manager.
-     X200S is a "Flip-Flop" style USB modem and as such registers as USB Storage when plugged in, so I believe it requires "USB_MODESWITCH" in order to work.
-     USB_MODESWITCH.CONF file is as follows:
# Alcatel X200/X060S
DefaultVendor= 0x1bbb
DefaultProduct= 0xf000
        
TargetVendor= 0x1bbb
TargetProduct= 0x0000
                       MessageContent="55534243123456788000000080000606f504025270000000000000000000"

-      lsusb -v -d:f000     shows the USB device as Mass Storage initially:

        Bus 005 Device 004: ID 1bbb:f000  
        Device Descriptor:
          bLength                18
          bDescriptorType         1
          bcdUSB               2.00
          bDeviceClass            0 (Defined at Interface level)
          bDeviceSubClass         0 
          bDeviceProtocol         0 
          bMaxPacketSize0        64
          idVendor           0x1bbb 
          idProduct          0xf000 
          bcdDevice            0.00
          iManufacturer           3 
          iProduct                2 
          iSerial                 4 
          bNumConfigurations      1
          Configuration Descriptor:
            bLength                 9
            bDescriptorType         2
            wTotalLength           32
            bNumInterfaces          1
            bConfigurationValue     1
            iConfiguration          1 
            bmAttributes         0xa0
              (Bus Powered)
              Remote Wakeup
            MaxPower              500mA
            Interface Descriptor:
              bLength                 9
              bDescriptorType         4
              bInterfaceNumber        0
              bAlternateSetting       0
              bNumEndpoints           2
              bInterfaceClass         8 Mass Storage
              bInterfaceSubClass      6 SCSI
              bInterfaceProtocol     80 Bulk (Zip)

-     When you execute USB_MODESWITCH the following is displayed:
        sudo usb_modeswitch

        Looking for target devices ...
         No devices in target mode or class found
        Looking for default devices ...
         Found default devices (1)
        Accessing device 004 on bus 005 ...
        Using endpoints 0x01 (out) and 0x81 (in)
        Inquiring device details; driver will be detached ...
        Looking for active driver ...
         OK, driver found ("usb-storage")
         OK, driver "usb-storage" detached
        
        Received inquiry data (detailed identification)
        -------------------------
          Vendor String: USBModem
           Model String: MMC Storage     
        Revision String: 2.31
        -------------------------
        
        Device description data (identification)
        -------------------------
        Manufacturer: USBModem
             Product: HSPA Data Card
          Serial No.: 1234567890ABCDEF
        -------------------------
        Setting up communication with interface 0 ...
        Trying to send the message to endpoint 0x01 ...
         OK, message successfully sent
        Run lsusb to note any changes. Bye.

-      lsusb shows no difference to vendor/product:

        Bus 005 Device 004: ID 1bbb:f000  
        Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
        Bus 005 Device 002: ID 064e:a129 Suyin Corp. 
        Bus 005 Device 001: ID 0000:0000  
        Bus 004 Device 001: ID 0000:0000  
        Bus 003 Device 001: ID 0000:0000  
        Bus 002 Device 001: ID 0000:0000  
        Bus 001 Device 001: ID 0000:0000 

-     sudo modprobe usbserial vendor=0x1bbb product=0x0000   (produces no response)
-     lsmod|grep usb (not sure what this does but maybe the info is useful??)
        usbserial              35688  0 
        hci_usb                16540  0 
        bluetooth              60772  5 hci_usb,rfcomm,l2cap
        usbhid                 32256  0 
        hid                    38912  1 usbhid

-     I cannot get any further than this...dmesg|grep usb shows the following (Note: "generic converter now attached to ttyUSB0" which looks good but "usbserial_generic 5-8:1.0: device disconnected"):

dmesg|grep usb
[   41.239034] usbcore: registered new interface driver usbfs
[   41.239114] usbcore: registered new interface driver hub
[   41.239204] usbcore: registered new device driver usb
[   42.866289] usb usb1: configuration #1 chosen from 1 choice
[   42.968995] usb usb2: configuration #1 chosen from 1 choice
[   43.072907] usb usb3: configuration #1 chosen from 1 choice
[   43.176800] usb usb4: configuration #1 chosen from 1 choice
[   43.280298] usbcore: registered new interface driver usb-storage
[   43.280381] usbcore: registered new interface driver libusual
[   44.794856] usbcore: registered new interface driver hiddev
[   44.794938] usbcore: registered new interface driver usbhid
[   44.794945] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   44.831950] usb usb5: configuration #1 chosen from 1 choice
[   45.322197] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   45.509270] usb 5-2: configuration #1 chosen from 1 choice
[   45.753897] usb 5-3: new high speed USB device using ehci_hcd and address 3
[   45.898286] usb 5-3: configuration #1 chosen from 1 choice
[   45.904344] usb-storage: device found at 3
[   45.904353] usb-storage: waiting for device to settle before scanning
[   50.494642] usb-storage: device scan complete
[   69.968787] usbcore: registered new interface driver hci_usb
[   70.396040] usbcore: registered new interface driver uvcvideo
[   70.467745] usbcore: registered new interface driver cdc_acm
[   70.468289] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/class/cdc-acm.c: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   70.505516] usbcore: registered new interface driver cdc_ether
[   70.536104] usbcore: registered new interface driver mbm
[  392.013884] usb 5-8: new high speed USB device using ehci_hcd and address 4
[  392.159365] usb 5-8: configuration #1 chosen from 1 choice
[  392.166871] usb-storage: device found at 4
[  392.166890] usb-storage: waiting for device to settle before scanning
[  397.162477] usb-storage: device scan complete
[  599.573765] usb 5-8: usbfs: process 5736 (usb_modeswitch) did not claim interface 0 before use
[  741.875766] usbcore: registered new interface driver usbserial
[  741.877280] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  741.880574] usbserial_generic 5-8:1.0: generic converter detected
[  741.882408] usb 5-8: generic converter now attached to ttyUSB0
[  741.884019] usbcore: registered new interface driver usbserial_generic
[  741.884033] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 8855.969980] usb 5-8: USB disconnect, address 4
[ 8855.971127] usbserial_generic 5-8:1.0: device disconnected

-     /etc/wvdial.conf is as follows:
        [Dialer Defaults]
        Init1 = ATZ
        Init2 = ATQ0 V1 E1 +FCLASS=0
        Modem Type = Analog Modem
        Baud = 3600000
        New PPPD = yes
        Modem = /dev/ttyUSB0
        ISDN = 0
        
        [Dialer pin]
        Dial Command = ATDT
        Init1 = ATZ
        Init2 = AT+CPIN=
        
        [Dialer virgin]
        Init1 = ATZ
        Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
        Init3 = 
        Init4 = AT+CGDCONT=1,"IP","goto.virginmobile.uk","",0,0
        Baud = 3600000
        Username = off
        Password = off
        Phone = *99#
        Dial Command = ATDT
        Stupid Mode = 1
        Compuserve = 0
        Force Address =
        Idle Seconds = 0
        Carrier Check = No
        ISDN = 0
        Auto DNS = 1
        Remote Name = "*"

-               Finally, executing wvdial gets somewhere...but not far enough!!

 wvdial virgin
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

---

### Post by GeorgeVita on 2010-01-02
Hi **DavidHOB**, welcome to this forum!

The 'closer to solution' post for your modem is: [http://ubuntuforums.org/showpost.php?p=7597641&postcount=6](http://ubuntuforums.org/showpost.php?p=7597641&postcount=6)

Your problem possibly is that you did not switch it successfully and/or the communication port did not configured.

Try the following procedure:
- Boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem, **wait** 30 seconds
- DO NOT use usb-modeswitch now
- from terminal: **dmesg**
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and post it here.
>>> We need to see any cd-rom created as **sr0**, sr1, ...
- If so you can try to eject it: **sudo eject sr0**
- **wait** 10 seconds
- check **dmesg** and **lsusb** for the requested **1bbb:0000**
- If you did not see **1bbb:0000** try usb-modeswitch, **wait** some seconds and test **lsusb** once again

Post any progress to follow up.
Regards,
George

---

### Post by DavidHOB on 2010-01-02
Many thanks George, it's good to hear from you. I have done as you have suggested, following your requests exactly, and have posted the output below. Thank you for your help, I am grateful for your time.

- Second "dmesg" executed after plugging in the device:

 dmesg
[ 2566.556869] usb 5-1: new high speed USB device using ehci_hcd and address 4
[ 2566.702396] usb 5-1: configuration #1 chosen from 1 choice
[ 2566.706915] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2566.720468] usb-storage: device found at 4
[ 2566.720487] usb-storage: waiting for device to settle before scanning
[ 2571.713842] usb-storage: device scan complete
[ 2571.716732] scsi 3:0:0:0: CD-ROM            USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2571.727979] sr0: scsi-1 drive
[ 2571.728000] Uniform CD-ROM driver Revision: 3.20
[ 2571.731911] sr 3:0:0:0: Attached scsi CD-ROM sr0
[ 2571.734284] sr 3:0:0:0: Attached scsi generic sg2 type 5
[ 2572.543827] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2572.546453] ISOFS: changing to secondary root

- "sudo eject sr0" executed, then dmesg again:

 dmesg
[ 2566.556869] usb 5-1: new high speed USB device using ehci_hcd and address 4
[ 2566.702396] usb 5-1: configuration #1 chosen from 1 choice
[ 2566.706915] scsi3 : SCSI emulation for USB Mass Storage devices
[ 2566.720468] usb-storage: device found at 4
[ 2566.720487] usb-storage: waiting for device to settle before scanning
[ 2571.713842] usb-storage: device scan complete
[ 2571.716732] scsi 3:0:0:0: CD-ROM            USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2571.727979] sr0: scsi-1 drive
[ 2571.728000] Uniform CD-ROM driver Revision: 3.20
[ 2571.731911] sr 3:0:0:0: Attached scsi CD-ROM sr0
[ 2571.734284] sr 3:0:0:0: Attached scsi generic sg2 type 5
[ 2572.543827] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2572.546453] ISOFS: changing to secondary root

- lsusb results:

lsusb
Bus 005 Device 004: ID 1bbb:f000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 064e:a129 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

- tried usb_modeswitch:

 usb_modeswitch

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 000 on bus 005 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

Device description data (identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
 Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye.

- tried lsusb again...no change:

lsusb
Bus 005 Device 004: ID 1bbb:f000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 064e:a129 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by DavidHOB on 2010-01-02
....just to add, I just tried sudo usb_modeswitch...

sudo usb_modeswitch

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 005 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: USBModem
   Model String: MMC Storage     
Revision String: 2.31
-------------------------

Device description data (identification)
-------------------------
Manufacturer: USBModem
     Product: HSPA Data Card
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

- this looks better but I am still getting f000 as the device in lsusb!!

---

### Post by GeorgeVita on 2010-01-03
Hi **DavidHOB**,

>>> EDIT: after 'sudo eject sr0' needs some seconds (10-15) before retrying dmesg

the possible 'explanation' to have 0xf000 after eject/usb_modeswitch is that device comes back as CD-ROM which is not bad if it 'passes' via 'modem mode'. Issue an extra command before eject or usb_modeswitch to 'catch' 0x000 for com-port assignment: ```
sudo modprobe usbserial vendor=0x1bbb product=0x0000
``` Success is when you can find /dev/ttyUSBx ports using the command: ```
ls /dev/ttyU*
```
Retry and post results.

G

---

### Post by DavidHOB on 2010-01-03
Thanks George. I have tried everything in your post and lsusb still shows f000 as the device address and no TTYUSB0 seems to be created. (I am waiting at least 30 seconds before executing each stage). Please see details below:

Second dmesg:

dmesg
[  695.744672] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  695.890145] usb 5-1: configuration #1 chosen from 1 choice
[  695.894097] scsi3 : SCSI emulation for USB Mass Storage devices
[  695.895625] usb-storage: device found at 4
[  695.895644] usb-storage: waiting for device to settle before scanning
[  700.889346] usb-storage: device scan complete
[  700.891630] scsi 3:0:0:0: CD-ROM            USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
[  700.901679] sr0: scsi-1 drive
[  700.901699] Uniform CD-ROM driver Revision: 3.20
[  700.901926] sr 3:0:0:0: Attached scsi CD-ROM sr0
[  700.902108] sr 3:0:0:0: Attached scsi generic sg2 type 5
[  701.730460] ISO 9660 Extensions: Microsoft Joliet Level 3
[  701.733494] ISOFS: changing to secondary root


THEN : sudo modprobe usbserial vendor=0x1bbb product=0x0000

THEN : sudo eject sr0

- ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory

- lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 1bbb:f000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a129 Suyin Corp. 

-  sudo usb_modeswitch

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 005 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: USBModem
   Model String: MMC Storage     
Revision String: 2.31
-------------------------

Device description data (identification)
-------------------------
Manufacturer: USBModem
     Product: HSPA Data Card
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

-  lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 1bbb:f000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a129 Suyin Corp. 

-  executed "dmesg" again and the following had been added to the previous dmesg content:

[  166.909839] usbcore: registered new interface driver usbserial
[  166.912766] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  166.918861] usbcore: registered new interface driver usbserial_generic
[  166.918884] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  308.586513] usb 5-1: usbfs: process 5525 (usb_modeswitch) did not claim interface 0 before use


-  I have a utility called USB VIEWER which displays details on the USB devices attached. At this point, the device is listed as "HSPA Data Card" and details as follows:

HSPA Data Card
Manufacturer: USBModem
Serial Number: 1234567890ABCDEF
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 1bbb
Product Id: f000
Revision Number:  0.00

Config Number: 1
    Number of Interfaces: 1
    Attributes: a0
    MaxPower Needed: 500mA

    Interface Number: 0
        Name: (none)
        Alternate Number: 0
        Class: 08(stor.) 
        Sub Class: 06
        Protocol: 50
        Number of Endpoints: 2

            Endpoint Address: 01
            Direction: out
            Attribute: 2
            Type: Bulk
            Max Packet Size: 512
            Interval: 0ms

            Endpoint Address: 81
            Direction: in
            Attribute: 2
            Type: Bulk
            Max Packet Size: 512
            Interval: 0ms

-  Last lsusb & ls tests:
lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 1bbb:f000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a129 Suyin Corp. 

ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory

Kind regards,


David.

---

### Post by GeorgeVita on 2010-01-03
Hi David, I feel that if you do not get 1bbb:0000 at lsusb this modem cannot be used.

> **michelefrost said:**
> ... with a simple *dmesg*) you should now see:```
.....  Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
```This Direct-Access (instead of previous CD-ROM) means that we made it.
Next step is starting a driver for the modem. The command is:
```
modprobe usbserial vendor=0x1bbb product=0x0000

```In your dmesg / syslog you should see:```
Jul 11 10:24:16 eee-yard kernel: [  100.388222] usb 1-2: configuration #1 chosen from 1 choice
Jul 11 10:24:16 eee-yard kernel: [  100.390492] usbserial_generic 1-2:1.0: generic converter detected
Jul 11 10:24:16 eee-yard kernel: [  100.390658] usb 1-2: generic converter now attached to ttyUSB0
Jul 11 10:24:16 eee-yard kernel: [  100.390952] usbserial_generic 1-2:1.1: generic converter detected
Jul 11 10:24:16 eee-yard kernel: [  100.391068] usb 1-2: generic converter now attached to ttyUSB1
Jul 11 10:24:16 eee-yard kernel: [  100.394230] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 11 10:24:16 eee-yard kernel: [  100.395689] usbserial_generic 1-2:1.3: generic converter detected
Jul 11 10:24:16 eee-yard kernel: [  100.395847] usb 1-2: generic converter now attached to ttyUSB2

```

I am not familiar with **usb_modeswitch** (**we need an expert here!**) but the 'switching' seems that is NOT done:
> Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
OK, message successfully sent
-> Run lsusb to note any changes. Bye.
 > 
[ 308.586513] usb 5-1: usbfs: process 5525 (usb_modeswitch) did not claim interface 0 before use
Also the 'non-working' eject (not shown into dmesg) is a problem or conflict with usb_modeswitch. System should show an error message if could not 'eject it' or report it when done.

Other idea is to manually remove usb-storage and usbserial driver, then issue the new usbserial parameters, attach modem, use usb_modeswitch  and check results:
```
sudo modprobe -r usb-storage
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1bbb product=0x0000
... usb_modeswitch ...
dmesg
lsusb

```
Regards,
George

P.S. this modem still have problems on [karmic]("https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/479343")

---

### Post by DavidHOB on 2010-01-05
Thanks George,
 
You gave me the inspiration to hunt down the f000 -> 0000 problem and it is now fixed (see below) but I STILL cannot connect. I think my only issue left is to get WVDIAL working and it's a very dark art that I do not understand!!!
 
To fix the device issue I searched and found the main home site for USB_MODESWITCH (draisberghof) and read it all. I could see that my modem is supported and should switch from f000 to 0000. I downloaded and installed the latest USB_MODESWITCH and CONF file (released in December). It worked a treat.
 
Now, when I use wvdial my modem light states that it is connected, but I cannot ping or connect to the internet, and then wvdial times out (after a while).
 
To recap, I switch on my computer and do the following:
 
sudo dmesg -c
sudo modprobe usbserial vendor=0x1bbb product=0x0000
sudo usb_modeswitch
lsusb (to check f000 has become 0000)
 
I now have a modem that has 1bbb as the Vendor and 0000 as the Product attached to ttyUSB0, ttyUSB1 and ttyUSB2. (I believe ttyUSB1 is the key device).
 
DMESG shows the following:
 
[ 549.302753] usbcore: registered new interface driver usbserial
[ 549.304453] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 549.307705] usbcore: registered new interface driver usbserial_generic
[ 549.307719] /build/buildd/linux-2.6.24/debian/build/custom-source-lpia/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 555.418831] usb 5-1: usbfs: process 5730 (usb_modeswitch) did not claim interface 0 before use
[ 556.005320] usb 5-1: USB disconnect, address 2
[ 556.371823] usb 5-1: new high speed USB device using ehci_hcd and address 6
[ 556.536415] usb 5-1: configuration #1 chosen from 1 choice
[ 556.551446] usbserial_generic 5-1:1.0: generic converter detected
[ 556.551780] usb 5-1: generic converter now attached to ttyUSB0
[ 556.552178] usbserial_generic 5-1:1.1: generic converter detected
[ 556.552418] usb 5-1: generic converter now attached to ttyUSB1
[ 556.562753] scsi5 : SCSI emulation for USB Mass Storage devices
[ 556.569362] usbserial_generic 5-1:1.3: generic converter detected
[ 556.569719] usb 5-1: generic converter now attached to ttyUSB2
[ 556.570201] usb-storage: device found at 6
[ 556.570212] usb-storage: waiting for device to settle before scanning
[ 561.564336] usb-storage: device scan complete
[ 561.566390] scsi 5:0:0:0: Direct-Access USBModem MMC Storage 2.31 PQ: 0 ANSI: 2
[ 561.572591] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[ 561.572771] sd 5:0:0:0: Attached scsi generic sg1 type 0
 
 
I then try to dial using: 
 
sudo wvdial virgin
 
with output as follows:
 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: AT+CGDCONT=1,"IP","goto.virginmobile.uk","",0,0
AT+CGDCONT=1,"IP","goto.virginmobile.uk","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
--> Timed out while dialing. Trying again.
--> Disconnecting at Tue Jan 5 22:25:36 2010
 
The wvdial.conf (based on the Alcatel wvdial.conf on the odkq website) is as follows:
 
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB1
ISDN = 0
[Dialer pin]
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+CPIN=
[Dialer virgin]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = 
Init4 = AT+CGDCONT=1,"IP","goto.virginmobile.uk","",0,0
Baud = 3600000
Username = off
Password = off
Phone = *99#
Dial Command = ATDT
Timeout = 60
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 0
Carrier Check = no
ISDN = 0
Auto DNS = 1
Remote Name = "*"
 
 
After executing the wvdial command, the following has been added to DMESG:
 
[  736.424910] usb 5-1: reset high speed USB device using ehci_hcd and address 6
[  751.522883] usb 5-1: device descriptor read/64, error -110
[  765.446095] generic ttyUSB1: usb_serial_generic_write - failed submitting write urb, error -19
[  766.725827] usb 5-1: device descriptor read/64, error -110
[  766.940607] usb 5-1: reset high speed USB device using ehci_hcd and address 6
[  782.038612] usb 5-1: device descriptor read/64, error -110
[  797.240507] usb 5-1: device descriptor read/64, error -110
[  797.456349] usb 5-1: reset high speed USB device using ehci_hcd and address 6
[  807.854699] usb 5-1: device not accepting address 6, error -110
[  807.966615] usb 5-1: reset high speed USB device using ehci_hcd and address 6
[  818.364950] usb 5-1: device not accepting address 6, error -110
[  818.365058] usb 5-1: USB disconnect, address 6
[  818.366092] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  818.366176] usbserial_generic 5-1:1.0: device disconnected
[  818.367200] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[  818.367289] usbserial_generic 5-1:1.1: device disconnected
[  818.369115] scsi 5:0:0:0: Device offlined - not ready after error recovery
[  818.370859] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[  818.371292] usbserial_generic 5-1:1.3: device disconnected
[  818.373982] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374027] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374060] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374091] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374112] scsi 5:0:0:0: [sdd] READ CAPACITY failed
[  818.374122] scsi 5:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  818.374142] scsi 5:0:0:0: [sdd] Sense not available.
[  818.374166] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374188] scsi 5:0:0:0: [sdd] Write Protect is off
[  818.374201] scsi 5:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  818.374212] scsi 5:0:0:0: [sdd] Assuming drive cache: write through
[  818.374235] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374275] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374306] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374337] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374366] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374387] scsi 5:0:0:0: [sdd] READ CAPACITY failed
[  818.374397] scsi 5:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  818.374416] scsi 5:0:0:0: [sdd] Sense not available.
[  818.374439] scsi 5:0:0:0: rejecting I/O to dead device
[  818.374460] scsi 5:0:0:0: [sdd] Write Protect is off
[  818.374472] scsi 5:0:0:0: [sdd] Mode Sense: 00 00 00 00
[  818.374483] scsi 5:0:0:0: [sdd] Assuming drive cache: write through
[  818.374525] scsi 5:0:0:0: rejecting I/O to dead device
[  818.491066] usb 5-1: new high speed USB device using ehci_hcd and address 7
[  833.586844] usb 5-1: device descriptor read/64, error -110
[  848.788738] usb 5-1: device descriptor read/64, error -110
[  849.004529] usb 5-1: new high speed USB device using ehci_hcd and address 8
[  864.102557] usb 5-1: device descriptor read/64, error -110
[  879.304474] usb 5-1: device descriptor read/64, error -110
[  879.520277] usb 5-1: new high speed USB device using ehci_hcd and address 9
[  889.918593] usb 5-1: device not accepting address 9, error -110
[  890.030517] usb 5-1: new high speed USB device using ehci_hcd and address 10
[  900.428851] usb 5-1: device not accepting address 10, error -110
[  910.966088] usb 5-8: USB disconnect, address 5
[  910.967187] Buffer I/O error on device sdc1, logical block 497
[  910.967212] lost page write due to I/O error on sdc1

 
 
Kind regards,
 
 
David.

---

### Post by GeorgeVita on 2010-01-06
Hi, as you have the correct 'modem state': > **michelefrost said:**
> ...Now we have 3 serial usb interfaces! - **our modem is on USB2**.
Try the following /etc/wvdial.conf

```
[Dialer Defaults]
Modem Type = Analog Modem
Modem = /dev/ttyUSB2
Baud = 3600000
ISDN = 0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","goto.virginmobile.uk","",0,0
Username = off
Password = off
Phone = *99#
Stupid Mode = 1

```

Your SIM PIN check must be disabled. Use **sudo wvdial** to connect. Disconnect by pressing **CTRL-C** at the 'connection' terminal window. Check and remove 'offline mode' of firefox **ctrl-F W**

>>> Most info from: [http://ubuntuforums.org/showpost.php?p=7597641&postcount=6](http://ubuntuforums.org/showpost.php?p=7597641&postcount=6)

Regards,
George

---

### Post by DavidHOB on 2010-01-06
SOLVED!!!!
 
George, you're a genius! Thanks for that, the wvdial.conf worked a treat. I am now happily collecting my backed-up emails on my Ubuntu laptop. Thanks for all your help and really clear instruction.
 
Kind regards,
 
 
 
David.

---

### Post by pistacoppu on 2010-01-29
Even if it is marked as solved, i confirm that this wvdial.conf works.
I didn't need to do al the previous process because in "lsusb" my modem was recognized as 0000 not f000.
Ciao, and thanks

---

### Post by pdc on 2010-01-29
thanks pistacoppu; glad to hear it all worked so well

so you just plug your device into a standard Karmic 9.10; ??

(you have not installed usb_modeswitch etc ????)

and you can dial with wvdial ??

what does 

> uname -r give from a terminal?

can you copy and paste the result back here please: I assume you are running a 2.6.31.17 kernel?

---

### Post by pistacoppu on 2010-01-31
Hi pdc
i'm sorry but what i wrote was wrong: i thought that i did all the process and that it hadn't any effect but it had, because after installing  ubuntu 64bit instead of 32(on which i installed the x200s first), and typing lsusb the result was f000 and not 0000.
That is why i wrote that message before. i'm sorry for giving you a bad info.
_So i'm in your same situation_, that is the meaning of that grammatically horrible sentence in the beginning of that post.
But i can tell you one more thing: that the first time i followed all the commands described in that thread, on a fresh ubuntu 9.10 64, network manager recognized my modem, and i connected through it.
That appened only the first time, i don't know why, just the first connection.
In fact now i must connect through wvdial and not NM.

andrea@laptop:~$ uname -r
2.6.31-17-generic

---

### Post by pdc on 2010-01-31
thanks;

so you use usb_modeswitch to flip the modem, and then dial with wvdial?  and connect fine?

I think wvdial is just fine for me;

---

### Post by pistacoppu on 2010-02-01
> **pdc said:**
> 
so you use usb_modeswitch to flip the modem, and then dial with wvdial?  and connect fine?


yes.

do you know how to stop wvdial, if i accidentally close the terminal? is there something like: kilall wvdial?

---

### Post by pdc on 2010-02-02
the command is control-c from within the terminal; 

best idea is to NOT close the terminal whilst running wvdial;

if you do .......... don't know ........

sounds like something google might be able to tell you;

---

### Post by pistacoppu on 2010-02-24
the command to disconnect is
$ sudo killall pppd
and to close the terminal without losing the connection you have to use nohup:
$ sudo nohup wvdial
once it is connected you can close the terminal

---


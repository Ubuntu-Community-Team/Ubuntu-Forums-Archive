---
title: "connecting Tata Docomo USB Modem in Ubuntu 10.04"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2011-07-22
I have a  USB Modem MMX 372 G to connect internet lsusb shows

```
  Bus 002 Device 002: ID 05c6:9000 Qualcomm, Inc. 
```

and following is /var/log/messages when I connect the USB modem and connect it for the first time  the USB modem 
> 
Jul 24 08:37:42 bond kernel: [  110.200159] usb 2-2: new high speed USB device using ehci_hcd and address 2
Jul 24 08:37:43 bond kernel: [  110.353219] usb 2-2: configuration #1 chosen from 1 choice
Jul 24 08:37:43 bond kernel: [  110.428596] Initializing USB Mass Storage driver...
Jul 24 08:37:43 bond kernel: [  110.428971] scsi4 : SCSI emulation for USB Mass Storage devices
Jul 24 08:37:43 bond kernel: [  110.429219] usbcore: registered new interface driver usb-storage
Jul 24 08:37:43 bond kernel: [  110.429223] USB Mass Storage support registered.
Jul 24 08:37:48 bond kernel: [  115.432060] scsi 4:0:0:0: CD-ROM            Micromax HSUPA Modem      2.31 PQ: 0 ANSI: 0
Jul 24 08:37:48 bond kernel: [  115.439083] sr1: scsi-1 drive
Jul 24 08:37:48 bond kernel: [  115.442025] sr 4:0:0:0: Attached scsi generic sg2 type 5
Jul 24 08:37:55 bond kernel: [  122.268742] sr: Sense Key : Hardware Error [current] 
Jul 24 08:37:55 bond kernel: [  122.268749] sr: Add. Sense: No additional sense information




after some Googling I came know about usb-modswitch and installed it via Synaptics.
The version installed is 
> usb_modeswitch --version

 * usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !


I use Ubuntu 10.04 my kernel is 

> 2.6.32-24-generic

after installing usb-modswitch lsusb shows
```
  Bus 002 Device **003**: ID 05c6:9000 Qualcomm, Inc. 
```

and  also 
 > tail -f /var/log/messages
shows
 
> Jul 23 07:56:35 bond kernel: [18305.683958] usbcore: registered new interface driver usbserial
Jul 23 07:56:35 bond kernel: [18305.684079] USB Serial support registered for generic
Jul 23 07:56:35 bond kernel: [18305.684950] usbserial_generic 2-2:1.0: generic converter detected
Jul 23 07:56:35 bond kernel: [18305.687166] usb 2-2: generic converter now attached to ttyUSB0
Jul 23 07:56:35 bond kernel: [18305.687194] usbserial_generic 2-2:1.1: generic converter detected
Jul 23 07:56:35 bond kernel: [18305.689045] usb 2-2: generic converter now attached to ttyUSB1
Jul 23 07:56:35 bond kernel: [18305.689076] usbserial_generic 2-2:1.3: generic converter detected
Jul 23 07:56:35 bond kernel: [18305.689615] usb 2-2: generic converter now attached to ttyUSB2
Jul 23 07:56:35 bond kernel: [18305.689712] usbcore: registered new interface driver usbserial_generic
Jul 23 07:56:35 bond kernel: [18305.689716] usbserial: USB Serial Driver core
 




 then I did 
>  root@bond:~# modprobe usbserial vendor=0x05c6 product=0x9000 



Next set of commands
 > dmesg | grep -e "modem"  -e "tty"  

 shows

> 
[    0.000000] console [tty0] enabled
[18305.687166] usb 2-2: generic converter now attached to ttyUSB0
[18305.689045] usb 2-2: generic converter now attached to ttyUSB1
[18305.689615] usb 2-2: generic converter now attached to ttyUSB2
 

then
 
root@bond:~# wvdialconf 
>  
 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: Micromax
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: Micromax
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB1.
Modem configuration written to /etc/wvdial.conf.
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

 

Now when I use wvdial 
then my system shows following output and hangs

> bond@bond:~/Downloads/docomo$ sudo wvdial
[sudo] password for bond: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99
+CSQ: 17,99


Like this it keeps on repeating above steps.
My service provider does not give a user name and password.

Here is my wvdial.conf file
> 
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99***1#
ISDN = 0
;Password =
New PPPD = yes
;Username =
Modem = /dev/ttyUSB1
Baud = 9600


Now I tried to connect to internet using nm-applet as described on this blog 
[http://ershadk.wordpress.com/2010/03/30/connect-tata-docomo-internet-in-ubuntu-9-04/](http://ershadk.wordpress.com/2010/03/30/connect-tata-docomo-internet-in-ubuntu-9-04/)
the connection was visible in nm-applet antenna icon but it failed to dial any thing for internet.







I had created a new connection in 
System-->Preferences-->Mobile Broadband-->Add ----here I had added Tata Docomo

but  the option in network applet to connect to mobile broadband did not appear.



the connection option in antenna applet for this new mobile broadband connection on system tray did appear but upon selecting it was not able to connect to internet.

Without installing usb-modeswitch this option was not coming.So I think some thing did  proceded but not fully.Which as per above links should have come if things went correctly.
In Windows same modem works correctly.

This time I checked further and found 
in > /etc/usb_modeswitch.d there is no file with >  05c6:9000  combination.





Some thing is still missing is that probably this 
[https://bbs.archlinux.org/viewtopic.php?id=93562](https://bbs.archlinux.org/viewtopic.php?id=93562)

so this time I created a file 

So I created >  /etc/usb_modeswitch.d/05c6:9000 
with following entries 
> DefaultVendor=  0x05c6
DefaultProduct= 0x9000

TargetVendor=   0x05c6
TargetProduct=  0x9000

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"


But it still failed.After this i did

> 
root@bond:~# usb_modeswitch -W -c /etc/usb_modeswitch.d/05c6\:9000 
Reading config file: /etc/usb_modeswitch.d/05c6:9000

 * usb-modeswitch: handle USB devices with multiple modes
 * Version 1.1.0 (C) Josua Dietze 2010
 * Based on libusb 0.1.12

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x05c6
DefaultProduct= 0x9000
TargetVendor=   0x05c6
TargetProduct=  0x9000
TargetClass=    not set

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
MessageEndpoint= not set
MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check disabled
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 008
usb_os_find_busses: Found 007
usb_os_find_busses: Found 006
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 008
usb_os_find_devices: Found 001 on 007
usb_os_find_devices: Found 001 on 006
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 005 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 004 on 003
skipped 1 class/vendor specific interface descriptors
skipping descriptor 0xFF
skipped 1 class/vendor specific endpoint descriptors
usb_os_find_devices: Found 003 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 003
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 003 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 003 on 001
skipping descriptor 0xFF
skipping descriptor 0xB
skipped 2 class/vendor specific endpoint descriptors
skipped 6 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
skipped 20 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 413c:8160
  searching devices, found USB ID 413c:8162
  searching devices, found USB ID 413c:8161
  searching devices, found USB ID 0a5c:4500
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 05c6:9000
   found matching vendor ID
   found matching product ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 0c45:6400
  searching devices, found USB ID 1d6b:0002
 Found devices in target mode or class (1)
Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 413c:8160
  searching devices, found USB ID 413c:8162
  searching devices, found USB ID 413c:8161
  searching devices, found USB ID 0a5c:4500
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 05c6:9000
   found matching vendor ID
   found matching product ID
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 0c45:6400
  searching devices, found USB ID 1d6b:0002
 Found default devices (1)
Accessing device 003 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry
USB error: error sending control message: Broken pipe
Error: could not get description string "product"

USB description data (for identification)
-------------------------
Manufacturer: Micromax
     Product: 
  Serial No.: 000000000
-------------------------
Looking for active driver ...
 OK, driver found ("usbserial_generic")
 OK, driver "usbserial_generic" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

But the nm-applet is failing to dial for this modem.


Here is the output of 
lsusb -v -d 05c6:9000

> Bus 002 Device 005: ID 05c6:9000 Qualcomm, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05c6 Qualcomm, Inc.
  idProduct          0x9000 
  bcdDevice            0.00
  iManufacturer           2 Micromax
  iProduct                1 
  iSerial                 3 1234567890ABCDEF
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          1 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
  bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
    Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
       Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled


My ISP does not uses a username and password so wvdial is failing also nm-applet is failing.

But I am able to connect to internet via same modem in Windows and do not give a username and password other than the default phone no to dial which is *99***1#
Let me know if some one has any clue for the same as what next to do?

---

### Post by jamesbon on 2011-07-23
Ok this problem has been solved 
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4849#4849](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4849#4849)
Two changes made it work

1) As given on this link 
[https://bbs.archlinux.org/viewtopic.php?id=93562](https://bbs.archlinux.org/viewtopic.php?id=93562)
I created /etc/usb_modeswitch.d/05c6\:9000 
incorporate suggestions above both links
```

########################################################
# Siptune LM-75 ("LinuxModem")

DefaultVendor= 0x05c6
DefaultProduct=0x9000

#TargetVendor=  0x05c6
#TargetProduct= 0x9000
**TargetClass=0xff**

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

```
As per suggestion on this link
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4849#4849](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4849#4849)
TargetCLass I have bolded that is one thing.

Also the wvdial.conf file which ```
wvdialconf
``` was creating was not a correct one i.e. some things had to be edited manually.
The modem in my case was detected at 
```

/dev/ttyUSB0
/dev/ttyUSB1
/dev/ttyUSB2
```
and in these only /dev/ttyUSB2 was the correct port for my modem rest port were for quality control.

This is clear from Josh's suggestion here
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4849#4849](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4849#4849) 
So the wvdial.conf which was generated as a result of wvdialconf command was 
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
;Password = 
ISDN = 0
;Username = 
New PPPD = yes
Phone = *99***1#
Modem = /dev/ttyUSB0
Baud = 9600

```
where as the correct one should be 
```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99***1#
ISDN = 0
Username = " "
Password = " "
Init1 = ATZ
Init3 = AT+CGDCONT=1,"IP","TATA.DOCOMO.INTERNET"
Modem = /dev/ttyUSB2
;Baud = 9600
Baud = 960000
Auto DNS = 1
Dial Command = ATDT
Carrier Check = yes
Stupid Mode = 1

```

In my case Baud rate is not correct I had manually changed that (I am still searching for correct one).
I have added Init3 commands and carrier information etc in  it.So if you come across this post and it does not work then try modifying /dev/ttyUSB2 with /dev/ttyUSB1 or /dev/ttyUSB0 etc or any other parameter which needed a change for you.

After making above changes I had to use following commands to connect 

1) ```
usb_modeswitch -W -c /etc/usb_modeserial.d/05c6\:9000
```
2) ```
modprobe usbserial vendor=0x05c6 product=0x9000
```
3) ```
wvdial
```

It  worked for me. 
So you can try these steps at your end.My Modem is Micromax MMX 372G.

---


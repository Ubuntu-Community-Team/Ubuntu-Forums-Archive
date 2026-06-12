---
title: "plz help me to install hsdpa/umts usb modem in ubuntu micromax mmx 300 g"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by sanjivpur on 2009-08-23
plz hep how to install & modeswitch the usbmodem in ubuntu/redhat (linux)
step by step
thanks in advance 
mr sanjiv kumar

bihar india 854301

---

### Post by shantanubhadoria on 2009-11-28
I am facing the same issue. there seem to be two usb modes on this device one where it acts as a external usb disk(with drivers for mac and windows) and other where it acts as the modem. the default mode is usb disk. how do we switch it to modem mode? I am looking for something in ubuntu that can do that. then maybe if the drivers for the modem is also not available we could look for a driver

---

### Post by shantanubhadoria on 2009-11-29
```
[28798.197854] scsi 14:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[28798.201912] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[28798.202597] sd 14:0:0:0: Attached scsi generic sg3 type 0
[28900.708107] ACPI: EC: missing confirmations, switch off interrupt mode.
[28958.436908] usb 1-3: USB disconnect, address 24
[28989.108108] usb 1-3: new high speed USB device using ehci_hcd and address 25
[28989.244341] usb 1-3: configuration #1 chosen from 1 choice
[28989.255680] scsi15 : SCSI emulation for USB Mass Storage devices
[28989.259294] usb-storage: device found at 25
[28989.259302] usb-storage: waiting for device to settle before scanning
[28994.257040] usb-storage: device scan complete
[28994.258003] scsi 15:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
[28994.261841] sr1: scsi-1 drive
[28994.262159] sr 15:0:0:0: Attached scsi CD-ROM sr1
[28994.262462] sr 15:0:0:0: Attached scsi generic sg3 type 5
[29046.753432] usb 1-3: usbfs: process 17808 (usb_modeswitch) did not claim interface 0 before use

```

Ok this is the output from my dmesg after I ran usb_modeswitch. but I can't find any ttyUSB* file when I do $ ls /dev/ 
am I doing something wrong??
here is the output of my usb_modeswitch command
```

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 028 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: USBModem
   Model String: Disk            
Revision String: 2.31
-------------------------

Device description data (identification)
-------------------------
Manufacturer: USB Modem
     Product: USB Modem
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

```
on running lsusb I get the following output
```
Bus 001 Device 029: ID 1c9e:9603  
```

so the productid has changed for the device correctly
I used following settings in /etc/usb_modeswitch.conf
```

##########
# Settings for Micromax MMX 300G USB Modem
##########
DefaultVendor = 0x1c9e
DefaultProduct = 0xf000

TargetVendor = 0x1c9e
TargetProduct = 0x9603

# only for reference
MessageEndpoint=0x01

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"


```
still on running wvdialconf i get the following output : 
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial



```
Any help/guidance is appreciated.
You can read my summary of what I did so far at the following address :

[http://www.shantanubhadoria.com/techno-blab/configuring-micromax-mmx-300g-airtel-3g-data-card-in-ubuntu](http://www.shantanubhadoria.com/techno-blab/configuring-micromax-mmx-300g-airtel-3g-data-card-in-ubuntu)

unfortunately at this point I am stuck since i cant get wvdial configure after this.

---

### Post by utkarsh009 on 2010-06-05
> **shantanubhadoria said:**
> ```
[28798.197854] scsi 14:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[28798.201912] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[28798.202597] sd 14:0:0:0: Attached scsi generic sg3 type 0
[28900.708107] ACPI: EC: missing confirmations, switch off interrupt mode.
[28958.436908] usb 1-3: USB disconnect, address 24
[28989.108108] usb 1-3: new high speed USB device using ehci_hcd and address 25
[28989.244341] usb 1-3: configuration #1 chosen from 1 choice
[28989.255680] scsi15 : SCSI emulation for USB Mass Storage devices
[28989.259294] usb-storage: device found at 25
[28989.259302] usb-storage: waiting for device to settle before scanning
[28994.257040] usb-storage: device scan complete
[28994.258003] scsi 15:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
[28994.261841] sr1: scsi-1 drive
[28994.262159] sr 15:0:0:0: Attached scsi CD-ROM sr1
[28994.262462] sr 15:0:0:0: Attached scsi generic sg3 type 5
[29046.753432] usb 1-3: usbfs: process 17808 (usb_modeswitch) did not claim interface 0 before use

```

Ok this is the output from my dmesg after I ran usb_modeswitch. but I can't find any ttyUSB* file when I do $ ls /dev/ 
am I doing something wrong??
here is the output of my usb_modeswitch command
```

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 028 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: USBModem
   Model String: Disk            
Revision String: 2.31
-------------------------

Device description data (identification)
-------------------------
Manufacturer: USB Modem
     Product: USB Modem
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.

```
on running lsusb I get the following output
```
Bus 001 Device 029: ID 1c9e:9603  
```

so the productid has changed for the device correctly
I used following settings in /etc/usb_modeswitch.conf
```

##########
# Settings for Micromax MMX 300G USB Modem
##########
DefaultVendor = 0x1c9e
DefaultProduct = 0xf000

TargetVendor = 0x1c9e
TargetProduct = 0x9603

# only for reference
MessageEndpoint=0x01

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"


```
still on running wvdialconf i get the following output : 
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial



```
Any help/guidance is appreciated.
You can read my summary of what I did so far at the following address :

[http://www.shantanubhadoria.com/techno-blab/configuring-micromax-mmx-300g-airtel-3g-data-card-in-ubuntu](http://www.shantanubhadoria.com/techno-blab/configuring-micromax-mmx-300g-airtel-3g-data-card-in-ubuntu)

unfortunately at this point I am stuck since i cant get wvdial configure after this.

I can tell you how to get rid of this. Plug in your device before starting your computer (by the way, i have micromax mmx 310g whose product id is 9605. for mmx 300g it is 9603.) enter "lsusb" in terminal if the product id is 9603 then use the command "sudo modprobe usbserial vendor=0x1c9e product=0x9603" then run "dmesg" it will display that your device is connected to ttyUSBn where n is a whole number. then you can configure it with wvdial. If your product id is f000 then you have to first run "sudo usb_modeswitch". Guess where i am stuck. when i run "sudo wvdial" it gets stuck and is not able to connect. Its just annoying. Thanks!

---

### Post by webtechpatna on 2010-07-02
[COLOR=#C00000][/COLOR] 
[COLOR=#C00000]i m able to change mode to usb modem device 9603[/COLOR]
[COLOR=#C00000][/COLOR] 
[COLOR=#C00000]but still got stuck with [/COLOR]
[COLOR=#C00000][/COLOR] 
[COLOR=#C00000]bharat@ubuntu:~$ sudo modprobe usbserial vendor=0x1c9e product=0×9603[/COLOR]
[COLOR=#C00000]FATAL: Error inserting usbserial (/lib/modules/2.6.31-14-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument[/COLOR]
 
 
plz help me out

---

### Post by utkarsh009 on 2010-07-02
type in the terminal: sudo gedit /etc/modules
then in the window which opens type(in a new line): usbserial vendor=0x1c9e product=0x9603
now reboot your computer
now you don't have to modprobe your device 
you can also try:
download sakis3g and use it for the connection. it works much better.
please post you results after trying each of the 2 methods

---


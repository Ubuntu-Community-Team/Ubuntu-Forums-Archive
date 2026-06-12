---
title: "Verizon um150vw no longer working EVDO"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by oolankaloophid on 2009-01-29
This worked flawlessly until Jan 28. Not sure if update broke it. When inserting the device it recognizes it but no longer creates /dev/ttyACM0. I am including the output of the relevant information.

*****lsusb*****
lsusb
**Bus 005 Device 008: ID 106c:3711 Curitel Communications, Inc. **
Bus 005 Device 007: ID 0bc2:2000 Seagate RSS LLC Storage Adapter V3 (TPP)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 005: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 003: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
*****end lsusb*****

*****dmesg*****
[ 4136.084063] usb 5-6: new high speed USB device using ehci_hcd and address 8
[ 4136.226220] usb 5-6: configuration #1 chosen from 1 choice
[ 4136.233350] scsi7 : SCSI emulation for USB Mass Storage devices
[ 4136.233820] usb-storage: device found at 8
[ 4136.233829] usb-storage: waiting for device to settle before scanning
[ 4138.499560] usbcore: registered new interface driver usbserial
[ 4138.501758] usbserial: USB Serial support registered for generic
[ 4138.501876] usbcore: registered new interface driver usbserial_generic
[ 4138.501885] usbserial: USB Serial Driver core
[ 4138.653905] usbserial: USB Serial support registered for GSM modem (1-port)
[ 4138.653993] option 5-6:1.0: GSM modem (1-port) converter detected
[ 4138.654233] usb 5-6: GSM modem (1-port) converter now attached to ttyUSB0
[ 4138.654269] option 5-6:1.1: GSM modem (1-port) converter detected
[ 4138.654412] usb 5-6: GSM modem (1-port) converter now attached to ttyUSB1
[ 4138.654447] option 5-6:1.2: GSM modem (1-port) converter detected
[ 4138.654576] usb 5-6: GSM modem (1-port) converter now attached to ttyUSB2
[ 4138.654605] usbcore: registered new interface driver option
[ 4138.654610] option: USB Driver for GSM modems: v0.7.2
[ 4138.774838] usbcore: registered new interface driver cdc_acm
[ 4138.775384] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 4141.232249] usb-storage: device scan complete
[ 4141.234495] scsi 7:0:0:0: Direct-Access     PANTECH  Mass Storage     0001 PQ: 0 ANSI: 0 CCS
[ 4141.238357] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 4141.238825] sd 7:0:0:0: Attached scsi generic sg3 type 0
*****end dmesg*****

*****lsusb -l (relevant device only)*****
Bus 005 Device 008: ID 106c:3711 Curitel Communications, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x106c Curitel Communications, Inc.
  idProduct          0x3711 
  bcdDevice            1.00
  iManufacturer           1 PANTECH
  iProduct                2 PANTECH USB MODEM
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          113
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      CDC Header:
        bcdCDC               1.09
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x0f
          connection notifications
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
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
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
*****lsusb -l*****

****/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi (relevant)*****
      <!-- Pantech -->
      <match key="@info.parent:usb.vendor_id" int="0x106c">
        <!-- PC5740, PC5750, UM150 EVDO rev A card, UM175 EVDO, UM175 EVDO rev A -->
        <match key="@info.parent:usb.product_id" int_outof="0x3701;0x3702;0x3711;0x3712;0x3714">
          <match key="@info.parent:usb.interface.number" int="0">
            <append key="modem.command_sets" type="strlist">IS-707-A</append>
          </match>
        </match>
      </match>
*****end /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi*****

*****wvdial*****
Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- 
PROGRAM HANGS AT THIS POINT
*****end wvdial*****


If anymore info is needed please let me know

Help mo Obi Wan Kenobi - youre my only hope

---

### Post by linuxr123 on 2009-01-30
I to have the same problem with kernel version 2.6.27-11.

---

### Post by mfb on 2009-01-31
I can confirm the issue. For now I am booting into 2.6.27-9 to make it work.

---

### Post by raparks on 2009-01-31
I just installed a week's worth of updates for Ubuntu 8.10 including the latest kernel today (01/31/2009).  Afterward, a Verizon UTStarcom UM150 VE broadband adapter would no longer work.  I tried the same adapter on another system on which the updates had already been installed, and no luck there either.  For the moment, I backed up the data, performed a clean Ubuntu 8.10 install with no updates, and am back to running fine.  Clearly the updates in the week or two leading up to 01/31/2009 are affecting some Verizon broadband adapters.

---

### Post by BartInTN on 2009-04-16
I had the same problem after a fresh install of 8.10, kernel 2.6.27-11.  The issue was resolved by updating to kernel 2.6.27-14.  Network manager worked with my Verizon aircard (106c:3711 Curitel) with no other mods, except for putting in my username and password.

As of 4/16/2009, one can upgrade the kernel with Synaptic:
System --> Administration --> Synaptic
Tools --> Repositories
Update Tab
Check the box by Pre-released update (intrepid-proposed)
Close and exit Synaptic
Approve the latest updates when they become available
Reboot when prompted

---


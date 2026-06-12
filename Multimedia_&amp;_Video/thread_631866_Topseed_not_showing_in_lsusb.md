---
title: "Topseed not showing in lsusb"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by danfig on 2007-12-04
Trying to understand why a lsusb without any arguments does not display discriptors for idVendor and idProduct, as does the Logitech USB mouse I have installed? Can you tell me how to edit the lirc_mceusb2.c to add this in?

Finally, would this be the reason the LINUXMCE AV Wizard says it does not see any Infared Device plugged in and the nice lady keeps repeating please plug in a compatible IRC device?


The * LIRC driver lirc_mceusb2 contains the 

#define VENDOR_TOPSEED          0x1784 

static struct usb_device_id usb_remote_table [] = {
{ USB_DEVICE(VENDOR_TOPSEED, 0x0001) },  /* Topseed eHome Infrared


Output from the lsusb -v

Bus 001 Device 005: ID 1784:0001 
Device Descriptor:
bLength 18
bDescriptorType 1
bcdUSB 1.10
bDeviceClass 0 (Defined at Interface level)
bDeviceSubClass 0 
bDeviceProtocol 0 
bMaxPacketSize0 16
idVendor 0x1784 
idProduct 0x0001 
bcdDevice 0.00
iManufacturer 1 Topseed
iProduct 2 eHome Infrared Transceiver
iSerial 3 TS0004Kr
bNumConfigurations 1
Configuration Descriptor:
bLength 9
bDescriptorType 2
wTotalLength 32
bNumInterfaces 1
bConfigurationValue 1
iConfiguration 0 
bmAttributes 0xa0
(Bus Powered)
Remote Wakeup
MaxPower 100mA
Interface Descriptor:
bLength 9
bDescriptorType 4
bInterfaceNumber 0
bAlternateSetting 0
bNumEndpoints 2
bInterfaceClass 255 Vendor Specific Class
bInterfaceSubClass 255 Vendor Specific Subclass
bInterfaceProtocol 255 Vendor Specific Protocol
iInterface 0 
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x01 EP 1 OUT
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0010 1x 16 bytes
bInterval 0
Endpoint Descriptor:
bLength 7
bDescriptorType 5
bEndpointAddress 0x81 EP 1 IN
bmAttributes 2
Transfer Type Bulk
Synch Type None
Usage Type Data
wMaxPacketSize 0x0010 1x 16 bytes
bInterval 0
Device Status: 0x0001
Self Powered

---

### Post by jmw86069 on 2008-06-22
Did you ever get an answer to your query? There are other threads with other (maybe related issues) with the lirc_mceusb2 driver, and I'm trying to follow those to help solve my problem. But I have the same problem. The vendor ID and product number are correct, and match with what is in the lirc_mceusb2.c file, but no vendor name. Also, yeah my remote isn't working in Ubuntu Hardy 8.04.

My symptoms:
1) It worked the first time, when it was the only USB device.
2) I updated drivers for my TV Tuner USB and upon adding it, the MCE remote stopped working. No lights came on the USB receiver.
3) I switched it off the USB hub (USB 2.0), to its own port (USB 1.1) and the lights come on, but nothing is getting through to linux somehow.
4) irw shows nothing.

Is the vendor name problem as aesthetic issue, or a symptom of something else causing real problems?

Thanks for any help!

Oh here's output from lsusb:
> Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 1784:0008
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 005: ID 1058:0910 Western Digital Technologies, Inc.
Bus 004 Device 004: ID 2304:0227 Pinnacle Systems, Inc. [hex]
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000

Bus 002 has the USB MCE receiver.

---


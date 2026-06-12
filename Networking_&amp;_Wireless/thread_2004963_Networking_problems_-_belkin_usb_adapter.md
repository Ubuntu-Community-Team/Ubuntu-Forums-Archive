---
title: "Networking problems - belkin usb adapter"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by holtfox on 2012-06-16
I am about to throw in the towel with Ubuntu.  

I have a belkin usb network adapter which works great until I remote into the machine using either ssh or rdp. I am able to remote into the machine once and after I log out, I have to reboot the Ubuntu box to be able to remote into the machine.  If I try to restart the network-manager service or ifconfig wlan0 down, those commands hang and I can't kill them.  I have to restart the machine in order to fix the network or unplug the adapter and plug into another port. 

I also have problems with torrents, I have to reduce the number of connections to 10 or else I have to restart the machine. 

Any suggestions??

---

### Post by Cheesehead on 2012-06-16
Please open a terminal, and post the kernel you are running ([FONT="Courier New"]uname -r[/FONT]) and the wireless dongle's entry from [FONT="Courier New"]lsusb -vv[/FONT].

---

### Post by holtfox on 2012-06-17
Please see the response below.  I removed some of the response from the lsusb -vv command that did not pertain to the network adapter.  If that is also important, let me know. 

```
uname -r    
3.2.0-25-generic

lsusb -vv

Bus 001 Device 003: ID 050d:905c Belkin Components F5D9050 Wireless G+ MIMO Network Adapter v4000 [Ralink RT2573]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x905c F5D9050 Wireless G+ MIMO Network Adapter v4000 [Ralink RT2573]
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

---


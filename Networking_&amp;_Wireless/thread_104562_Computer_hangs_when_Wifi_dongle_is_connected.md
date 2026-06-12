---
title: "Computer hangs when Wifi dongle is connected"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by Reggie on 2005-12-16
Hi,

whenever I boot with my wifi dongle (DWL-G122) inserted the computer hangs. .. this is the last thing I see:

...
Code: Bad EIP value.
ohci1394: already loaded
alim15x3: already loaded
....
ignoring pci display device 01:05.0
pci     [success]
usb
.. here it hangs. I'm using ndiswrapper for my dongle to work.

What can I do to fix this ?

---

### Post by Lambert on 2005-12-16
remove ndiswrapper from the /etc/modules file so it doesn't load that module and then put in your card. does it hang your computer now? Do not load ndiswrapper and run these commands.


sudo lshw 

and look for your card in the list. Post the output of that command here (just the section on your card, not the whole output as it will give info on every piece of hardware on your pc)

Also post the output of lspci -v   
same thing here, you can limit it to just the section on your card.

---

### Post by Reggie on 2005-12-18
Ok, so I've booted without ndiswrapper in my modulesfile. This worked idd.

Here's the info on the 3 USB controllers (don't know really wich is the one where my dongle is connected to)

lshw
> 
       *-usb:0
             physical id: b
             bus info: pci@00:0b.0
             version: 50
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd irq=10
        *-usb:1
             physical id: b.1
             bus info: pci@00:0b.1
             version: 50
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd irq=10
        *-usb:2
             physical id: b.2
             bus info: pci@00:0b.2
             version: 51
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd irq=11


lspci -v:
> 0000:00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company: Unknown device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 2000 [size=32]
	Capabilities: [80] Power Management version 2

0000:00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company: Unknown device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 2020 [size=32]
	Capabilities: [80] Power Management version 2

0000:00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company: Unknown device 0850
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at d4003000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2


---

### Post by Lambert on 2005-12-18
These are actually the usb connectors themselves and not the wireless dongle. I'm looking for the actual output of the dongle device.

---

### Post by Reggie on 2005-12-18
I started ndiswrapper, and tried these commando's again, but no info about the usb-stick whatsoever :s

---

### Post by Lambert on 2005-12-18
If you run this command does it show?

lsusb -v

---

### Post by Reggie on 2005-12-18
Yes, I think this is it:

> Bus 003 Device 002: ID 2001:3c00 D-Link Corp. [hex] 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2001 D-Link Corp. [hex]
  idProduct          0x3c00 
  bcdDevice            0.01
  iManufacturer           1 ANI 
  iProduct                2 802.11g W
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1



---

### Post by Reggie on 2005-12-19
Ok I've installed rt2500 (using the package file found on packages.ubuntu.com).. but is it an independent driver for my kind of wificard ? Or do I need ndiswrapper to load rt2500 ? Cause it aint working ;)

---

### Post by Lambert on 2005-12-20
That's not a correct driver for this device. Looking around some I don't believe there is currently a native driver that works for this.

(maybe the rt2570 or the newer rt2x000(beta) driver)

ndiswrapper is what you need to use but you  use the windows driver and not anything you install or download from ubuntu.

In my signataure there's a link to using ndiswrapper.

---

### Post by Reggie on 2005-12-20
I've figured it out that I need rt2570 idd ;) It worked for a moment, but now it doesn't anymore. I've started a new thread for this ..

---

### Post by Reggie on 2005-12-20
Ok I figured it out. It works now :) without ndiswrapper, I'm really glad I got rid of that one.

windows drivers on linux are damn evil

---


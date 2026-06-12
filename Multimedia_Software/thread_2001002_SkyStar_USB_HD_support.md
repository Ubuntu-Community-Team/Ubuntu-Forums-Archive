---
title: "SkyStar USB HD support"
date: 2012-06-10
forum: Multimedia Software
---

### Post by benandrews54 on 2012-06-10
Hi all,

I have recently installed Ubuntu 12.04 onto an old laptop and am trying to set things up. I'm a complete noob to Linux so hear me out :).

I have a SkyStar USB HD DVB-S tuner and want to get it running on my Linux machine. I had it working on my Windows 8 (Consumer Preview) laptop over Easter but since I have come back from uni for the summer it doesn't seem to work so thought I would try it in Linux.

When I plug it into my laptop nothing comes up in 'Computer' and the machine shows no sign of the device being connected at all so I am basically stuck from square one. I found this tutorial ([http://www.linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD](http://www.linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD)) but it doesn't seem to work.

Any help would be much appreciated

---

### Post by newpipe on 2012-07-30
Hi!
I'm also trying to get the Technisat SkyStar USB HD running on a Ubuntu 12.04. But until now I had no success.
After plugging the Receiver into the USB interface I get the following output:
```
mine@zentrale:~/temp/v4l$ lsusb Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 001 Device 010: ID 14f7:0500 TechniSat Digital GmbH DVB-PC TV Star HD Bus 001 Device 003: ID 1b1c:1a03 Corsair
```
```
mine@zentrale:~/temp/v4l$ lsusb -v -d 14f7:0500  Bus 001 Device 010: ID 14f7:0500 TechniSat Digital GmbH DVB-PC TV Star HD Couldn't open device, some information will be missing Device Descriptor:   bLength                18   bDescriptorType         1   bcdUSB               2.00   bDeviceClass            0 (Defined at Interface level)   bDeviceSubClass         0    bDeviceProtocol         0    bMaxPacketSize0        64   idVendor           0x14f7 TechniSat Digital GmbH   idProduct          0x0500 DVB-PC TV Star HD   bcdDevice            0.01   iManufacturer           1    iProduct                2    iSerial                 3    bNumConfigurations      1   Configuration Descriptor:     bLength                 9     bDescriptorType         2     wTotalLength           69     bNumInterfaces          1     bConfigurationValue     1     iConfiguration          0      bmAttributes         0xc0       Self Powered     MaxPower              300mA     Interface Descriptor:       bLength                 9       bDescriptorType         4       bInterfaceNumber        0       bAlternateSetting       0       bNumEndpoints           3       bInterfaceClass       255 Vendor Specific Class       bInterfaceSubClass      0        bInterfaceProtocol      0        iInterface              0        Endpoint Descriptor:         bLength                 7         bDescriptorType         5         bEndpointAddress     0x82  EP 2 IN         bmAttributes            2           Transfer Type            Bulk           Synch Type               None           Usage Type               Data         wMaxPacketSize     0x0200  1x 512 bytes         bInterval               0       Endpoint Descriptor:         bLength                 7         bDescriptorType         5         bEndpointAddress     0x81  EP 1 IN         bmAttributes            2           Transfer Type            Bulk           Synch Type               None           Usage Type               Data         wMaxPacketSize     0x0200  1x 512 bytes         bInterval               0       Endpoint Descriptor:         bLength                 7         bDescriptorType         5         bEndpointAddress     0x01  EP 1 OUT         bmAttributes            2           Transfer Type            Bulk           Synch Type               None           Usage Type               Data         wMaxPacketSize     0x0200  1x 512 bytes         bInterval               0     Interface Descriptor:       bLength                 9       bDescriptorType         4       bInterfaceNumber        0       bAlternateSetting       1       bNumEndpoints           3       bInterfaceClass       255 Vendor Specific Class       bInterfaceSubClass      0        bInterfaceProtocol      0        iInterface              0        Endpoint Descriptor:         bLength                 7         bDescriptorType         5         bEndpointAddress     0x82  EP 2 IN         bmAttributes            1           Transfer Type            Isochronous           Synch Type               None           Usage Type               Data         wMaxPacketSize     0x0c00  2x 1024 bytes         bInterval               1       Endpoint Descriptor:         bLength                 7         bDescriptorType         5         bEndpointAddress     0x81  EP 1 IN         bmAttributes            2           Transfer Type            Bulk           Synch Type               None           Usage Type               Data         wMaxPacketSize     0x0200  1x 512 bytes         bInterval               0       Endpoint Descriptor:         bLength                 7         bDescriptorType         5         bEndpointAddress     0x01  EP 1 OUT         bmAttributes            2           Transfer Type            Bulk           Synch Type               None           Usage Type               Data         wMaxPacketSize     0x0200  1x 512 bytes         bInterval               0
```
After plugging in the USB device I only get from dmesg:
```
[ 7302.444126] usb 1-4: new high-speed USB device number 10 using ehci_hcd
```
dmesg | grep -i dvb gives me nothing:
```
mine@zentrale:~$ dmesg | grep -i dvb mine@zentrale:~$
```
AFAIK this device should run out of the box. What can I do to get this USB device running on my Ubuntu system?
It would be really great if someone could give us some hints on that!

newpipe

---

### Post by newpipe on 2012-07-30
Hi!
Finally I got the Technisat SkyStar USB HD to work.

The problem was, that the needed kernel module was not loaded. To get that fixed I simply added the following line to /etc/modules:

"dvb-usb-technisat-usb2"

Best regards,
newpipe

---

### Post by Jungle_King on 2012-12-22
+1 from me too!

I had already done this - [http://www.linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD-](http://www.linuxtv.org/wiki/index.php/Technisat_SkyStar_USB_HD-) but it wasn't showing up in /dev. 

Added the line as recomended by newpipe, and it's there after a reboot. Thanks dude!

---

### Post by Jungle_King on 2012-12-23
Still having issues with this. 

When setting up the card within Myth, it automatically suggests it as the input device which is great. Ubuntu obviously recognises it as a DVB-S card. Dmesg gives this when i plug it in:

```
[80316.918801] dvb-usb: Technisat SkyStar USB HD (DVB-S/S2) successfully deinitialized and disconnected.
[80322.913438] usb 1-5: new high-speed USB device number 6 using ehci_hcd
[80323.046421] usb 1-5: New USB device found, idVendor=14f7, idProduct=0500
[80323.046433] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[80323.048142] technisat-usb2: set alternate setting
[80323.544858] dvb-usb: found a 'Technisat SkyStar USB HD (DVB-S/S2)' in cold state, will try to load a firmware
[80323.547852] dvb-usb: downloading firmware from file 'dvb-usb-SkyStar_USB_HD_FW_v17_63.HEX.fw'
[80323.631408] usb 1-5: USB disconnect, device number 6
[80323.631573] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[80325.386761] usb 1-5: new high-speed USB device number 7 using ehci_hcd
[80325.520679] usb 1-5: New USB device found, idVendor=14f7, idProduct=0500
[80325.520691] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[80325.520698] usb 1-5: Product: TechniSat USB device
[80325.520703] usb 1-5: Manufacturer: TechniSat Digital
[80325.520708] usb 1-5: SerialNumber: 0008C9F0AE3A
[80325.524867] technisat-usb2: set alternate setting
[80325.525011] technisat-usb2: firmware version: 17.63
[80325.525018] dvb-usb: found a 'Technisat SkyStar USB HD (DVB-S/S2)' in warm state.
[80325.525490] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[80325.525897] DVB: registering new adapter (Technisat SkyStar USB HD (DVB-S/S2))
[80325.527360] dvb-usb: MAC address: 00:08:c9:f0:ae:3a
[80325.650822] stv6110x_attach: Attaching STV6110x
[80325.652932] technisat-usb2: i2c-error: 60 = 7
[80325.723145] DVB: registering adapter 0 frontend 0 (Technisat SkyStar USB HD (DVB-S/S2))...
[80325.723362] Registered IR keymap rc-technisat-usb2
[80325.723536] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:12.2/usb1/1-5/rc/rc2/input12
[80325.723614] rc2: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:12.2/usb1/1-5/rc/rc2
[80325.723863] input: MCE IR Keyboard/Mouse (technisat-usb2) as /devices/virtual/input/input13
[80325.724780] rc rc2: lirc_dev: driver ir-lirc-codec (technisat-usb2) registered at minor = 0
[80325.724787] dvb-usb: schedule remote query interval to 100 msecs.
[80325.725229] dvb-usb: Technisat SkyStar USB HD (DVB-S/S2) successfully initialized and connected.

```

Save the setup, then try and scan for channels which fails  with the vague error - "Error parsing paramaters".

When I return to the card setup page, it has the error "frontend ID: Could not get card info for card /dev/dvb/adapter0/frontend0 Subtype: Unknown Error".

Not very helpful at all, and absolutely nothing online. Will open  thread within the myth forums to see if anybody there has any idea.

---


---
title: "Cannot mount Canon HF10 via USB"
date: 2008-12-23
forum: Multimedia Software
---

### Post by emanuel.landeholm on 2008-12-23
Hi!

I can't mount my Canon HF10 video recorder via USB.

When I attach device the following appears in /var/log/messages:

> Dec 23 16:17:35 jel-desktop usb 1-2: new high speed USB device using ehci_hcd and address 5
Dec 23 16:17:35 jel-desktop usb 1-2: configuration #1 chosen from 1 choice
Dec 23 16:17:35 jel-desktop scsi5 : SCSI emulation for USB Mass Storage devices
Dec 23 16:17:35 jel-desktop usb-storage: device found at 5
Dec 23 16:17:35 jel-desktop usb-storage: waiting for device to settle before scanning
Dec 23 16:17:40 jel-desktop scsi 5:0:0:0: Direct-Access     CANON    HF10             1.00 PQ: 0 ANSI: 2
Dec 23 16:17:40 jel-desktop sd 5:0:0:0: [sde] Attached SCSI removable disk
Dec 23 16:17:40 jel-desktop usb-storage: device scan complete


Looks like it cannot read the partition table on the disk. fdisk and parted come up empty on /dev/sde, if I double click the USB drive icon in gnome it says no media present.

The camera mounts correctly in windows xp.

lsusb -v gives:

> 
Bus 001 Device 005: ID 04a9:31a5 Canon, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04a9 Canon, Inc.
  idProduct          0x31a5 
  bcdDevice            1.00
  iManufacturer           1 CANON Inc.
  iProduct                2 Canon HF10
  iSerial                 6 0000000000000000000000019356FA00
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          5 Hi-Speed
    bmAttributes         0xc0
      Self Powered
    MaxPower               10mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              3 Removable Drive
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


I'd really like to be able to access the camera from Linux! :(

---

### Post by emanuel.landeholm on 2009-02-14
*bump*

A clarification: I'm trying to access the internal on chip memory. I haven't tried mounting the camera when equipped with an external SDHC card.

The only semi working solution I have is to access the camera from a virtual VMware windows xp. This works if I do rmmod usb_storage and let VMware handle the USB device. But this involves copying the data to a virtual disk and then moving the files to my physical disk and is quite error prone and time consuming...

---

### Post by tom17 on 2009-03-11
The only input I can give is that it works fine for me on 64 bit 8.10 Ubuntu.

Would you like me to give you my output from anything to maybe help diagnose?

And while we are at it, any luck playing back the vid?

Tom...

---

### Post by emanuel.landeholm on 2009-04-24
> **tom17 said:**
> The only input I can give is that it works fine for me on 64 bit 8.10 Ubuntu.

Would you like me to give you my output from anything to maybe help diagnose?

Tom...

M'kay. I'm on 32 bit. Not sure where to start, really... 

Could you post the output of

```
sudo fdisk -l /dev/sdx
```

where x is the letter assigned to the hf10 usb-storage device?

Also, could you try:

```
sudo dmesg | grep -A 10 sdx
```

(x as above)

> And while we are at it, any luck playing back the vid?

Actually, yes I have. However this is in my gentoo. I'm using mplayer svn and nvidias 180.44 driver.

cheers!

---


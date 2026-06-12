---
title: "mount iphone over USB?"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by JaggedOne on 2007-11-29
I want to mount my iphone on ubuntu. After a bit of googling, all the solutions I can find involve using SSH and mounting it wirelessly. Is there any way to mount an iphone over USB? It should be possible because whenever I plug it in ubuntu automatically detects all of my iphone's photos. I just can't get music transfers working.

---

### Post by Ek0nomik on 2007-11-29
> **JaggedOne said:**
> I want to mount my iphone on ubuntu. After a bit of googling, all the solutions I can find involve using SSH and mounting it wirelessly. Is there any way to mount an iphone over USB? It should be possible because whenever I plug it in ubuntu automatically detects all of my iphone's photos. I just can't get music transfers working.

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

That was all I could find, and it involves the steps you wish you avoid.

Remember, the iPhone is relatively new.

---

### Post by topgun98 on 2008-04-07
*bump*

This can be done with iPods, surely there's a way to mount the iPhone over USB.

Mounting over wifi is great, except that I'm on several different WLANs throughout the day and there's no way I can keep a static IP since they're all in different subnets.  Transferring over USB would be highly preferable.

Thanks in advance to anyone who can help!

---

### Post by Imre Mehesz on 2008-07-16
I just got my new iPhone (3g). 

- When I plug it in, ubuntu (8.04) recognizes that there IS something plugged in. 

- When I type **lsusb** i can see that there is an Apple Inc device, however I can't mount it.

- i tried this: **sudo mount /dev/sda1/ mnt/iphone** (created iphone library first of course) but something weird happened and I could see my whole local computer folder structure under /mnt/iphone/

Any ideas? - i am sure that the solution is not (that) far :)

iM

ps; ubuntu ROX :D

---

### Post by Maximander on 2008-07-16
> - i tried this: sudo mount /dev/sda1/ mnt/iphone (created iphone library first of course) but something weird happened and I could see my whole local computer folder structure under /mnt/iphone/

That's your system drive. In general then, expect external drives to show up as /dev/sdb1 or /dev/sdc1, etc. /dev/sda is your drive, and is already mounted at /.

Now, on the the interesting stuff:
I plug in my iPhone 3G and it doesn't automount. I look to mount it manually, but there's no node in /dev. Hmm..

Okay, I'll take a look at dmesg to see which device node to mount:
```

[  130.600510] usb 7-1: new high speed USB device using ehci_hcd and address 5
[  130.621439] usb 7-1: configuration #1 chosen from 3 choices

```

So the device exposes multiple profiles, and udev just picked the wrong one (camera rather than mass storage?), so it didn't create block device nodes?.

I guess I'll check lsusb to see what the iPhone exposes:
lsusb -v (snipped for length, see attached full version)
```


Bus 007 Device 013: ID 05ac:1292 Apple Computer, Inc. 
Device Descriptor:
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x1292 
  bcdDevice            0.01
  iManufacturer           1 Apple Inc.
  iProduct                2 iPhone
  iSerial                 3 foo
  bNumConfigurations      3
  Configuration Descriptor:
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          5 PTP
    Interface Descriptor:
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
      bInterfaceProtocol      1 Picture Transfer Protocol (PIMA 15470)
      iInterface              0 
      Endpoint Descriptor:
        bmAttributes            2
          Transfer Type            Bulk
          Usage Type               Data
      Endpoint Descriptor:
        bmAttributes            2
          Transfer Type            Bulk
          Usage Type               Data
      Endpoint Descriptor:
        bmAttributes            3
          Transfer Type            Interrupt
          Usage Type               Data
  Configuration Descriptor:
    iConfiguration          6 iPod USB Interface
    Interface Descriptor:
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      AudioControl Interface Descriptor:
        bDescriptorSubtype      1 (HEADER)
      AudioControl Interface Descriptor:
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        wTerminalType      0x0201 Microphone
      AudioControl Interface Descriptor:
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        wTerminalType      0x0101 USB Streaming
    Interface Descriptor:
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
    Interface Descriptor:
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      AudioStreaming Interface Descriptor:
        bDescriptorSubtype      1 (AS_GENERAL)
      AudioStreaming Interface Descriptor:
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
    Interface Descriptor:
      bInterfaceClass         3 Human Interface Device
        HID Device Descriptor:
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bmAttributes            3
          Transfer Type            Interrupt
          Usage Type               Data
  Configuration Descriptor:
    bConfigurationValue     3
    iConfiguration          7 PTP + Apple Mobile Device
    Interface Descriptor:
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
      bInterfaceProtocol      1 Picture Transfer Protocol (PIMA 15470)
      Endpoint Descriptor:
    Interface Descriptor:
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    254 
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      3
Device Status:     0x0000
  (Bus Powered)


```

So I'm not sure where, if at all, the thing is a mass storage device like an iPod usually is. Anyone know about this?
I'm hoping a quick udev trigger will fix everything, but I've exhausted my limited knowledge on the subject.

---

### Post by Maximander on 2008-07-16
/* removed redundant post */

---

### Post by Imre Mehesz on 2008-07-16
Thanks,

But I only have /dev/sda* I tried to mount all of them :) no luck!

btw, I did **lsusb -v** got pretty much the same result as *Maximander*. 

Anybody else had any luck?

iM

---

### Post by Maximander on 2008-07-18
Okay, so, looks like the deal is that apple decided to use a custom, non-exposed method of managing files on the device rather than just mounting it as a mass storage device.

They created windows and mac libraries (libmobiledevice.so) to allow software to interact with the iPhone FS, which on a non-jailbroken device is restricted to the media folder. 

There are Mac and Windows projects which use aforementioned library to allow file management, but as there is no library for linux yet, we're somewhat stuck.

The good news: there is a project working on a FUSE module to allow mounting an iPhone under linux without jailbreak/ssh/etc. 
[http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page](http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page)
He's currently working on reverse engineering USB traces to figure out the protocol libmobiledevice uses to talk to the device, so that he can create an equivalent library for linux. Once that's done, he can use the library and fuse to allow mounting the FS.

So, Apple decided to use a custom, proprietary protocol for which they released windows and mac drivers, but left us out in the cold (typical). In (typical) Linux fashion, some people are working on fixing that, and we should watch and wait for now, or better yet, get involved: if you can dual boot or run a VM, contribute to their efforts by sending in USB traces or help reverse engineer the protocol. Putting pressure on Apple to document the protocol can't hurt anything either.

Anyway, looks like that's as far as this is going for now though.

---

### Post by Sigudian on 2008-07-19
Oh Oh Oh, there is an opensource application in windows to brows the filesystem through a special browser(the program), if only someone with extensive driver coding experience(or something like that) could look into it.

the windows program is called iPhonebrowser [http://code.google.com/p/iphonebrowser/](http://code.google.com/p/iphonebrowser/)
the answer to mount the iPhone as a drive must be in this code (it worked on my none jailbreaked iPhone 3g)

---

### Post by Imre Mehesz on 2008-07-20
I think I'm going to wait until a native Linux help arrives and see where that project goes :) 

however I installed vista on my laptop through VMware but had problems with iTunes (unknown error occured!?)

Thanks,
iM

---


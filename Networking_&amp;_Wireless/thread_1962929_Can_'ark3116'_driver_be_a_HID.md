---
title: "Can 'ark3116' driver be a HID?"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by keyf on 2012-04-21
Hi all,

Recently I purchased a noname USB IR-receiver to connect my IR remote control to Ubuntu box. The device appears to be "Arkmicro Technologies Inc. USB to IrDA adapter [ARK3116T]" in lsusb. In kernel 3.0+ there's a driver module - ark3116 which gets autoloaded when I connect the receiver to USB. The problem is that I can't find any new input devices:
```
$ cat /proc/bus/input/devices | grep Name
N: Name="Power Button"
N: Name="Power Button"
N: Name="DELL DELL USB Keyboard"
N: Name="HDA NVidia HDMI/DP,pcm=9"
N: Name="HDA NVidia HDMI/DP,pcm=8"
N: Name="HDA NVidia HDMI/DP,pcm=7"
N: Name="HDA NVidia HDMI/DP,pcm=3"
```
and the IR-input device is a starting point in each and every "remote control config" HOW-TOs I see on the net.
I'm not a guru in Linux, but Google says that it's driver's duty to register a new input device when device connects. So if it doesn't happen in my case with ark3116 module, does it mean that the device won't work as a receiver for my IR-remote?  
Is there anything like 'generic USB-IR driver' I can use with HID interface available?

Thanks :)

---

### Post by chili555 on 2012-04-21
We wonder if you might not have better luck in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

However, we love a mystery and we'll take a stab at it.> the IR-input device is a starting point in each and every "remote control config" HOW-TOs I see on the net.May we see a link or two? Are there any clues here when you plug in the device and manipulate the keys?```
sudo cat /var/log/syslog | grep ark
lsusb
```Thanks.

---

### Post by keyf on 2012-04-22
> **chili555 said:**
> We wonder if you might not have better luck in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I just thought that since IR is wireless it make more sense to put it here, in Wireless forum :)
How do I move the thread? Haven't found anything like it in the thread menu...

> 
However, we love a mystery and we'll take a stab at it.May we see a link or two? 
Are there any clues here when you plug in the device and manipulate the keys?```
sudo cat /var/log/syslog | grep ark
lsusb
```Thanks.

I wanted to save some space here, so I narrowed it down to just ark3116 driver. But OK, here's the detailed info: 
- It's Ubuntu 11.10 (kernel 3.0.0.17) on IdeaCentre Q150 nettop.
- syslog output (when I plug the USB receiver in):
```
kernel: [  360.760076] usb 3-2: USB disconnect, device number 2
kernel: [  360.760337] ark3116 ttyUSB0: ark3116 converter now disconnected from ttyUSB0
kernel: [  360.760366] ark3116 3-2:0.0: device disconnected
kernel: [  375.540040] usb 3-2: new full speed USB device number 3 using uhci_hcd
kernel: [  375.702261] usb 3-2: config 0 descriptor??
kernel: [  375.705240] ark3116 3-2:0.0: ark3116 converter detected
kernel: [  375.720062] usb 3-2: ark3116 using IrDA mode
kernel: [  375.720348] usb 3-2: ark3116 converter now attached to ttyUSB0
```

- lsusb -v output (I cut out all the other devices but the receiver):

```
Bus 003 Device 003: ID 18ec:3118 Arkmicro Technologies Inc. USB to IrDA adapter [ARK3116T]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x18ec Arkmicro Technologies Inc.
  idProduct          0x3118 USB to IrDA adapter [ARK3116T]
  bcdDevice            0.01
  iManufacturer           1 ARKMICRO     
  iProduct                3 USB TO IRDA 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     0
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

As all I want is to be able to control XBMC media center installed on the machine with my remote, I'm trying to setup lirc to work with my IR receiver. And that's where the question about registering ark3116 device as an input device came from...

---

### Post by chili555 on 2012-04-22
> idVendor           0x18ec Arkmicro Technologies Inc.
  idProduct          0x3118 USB to IrDA adapter [ARK3116T]
  bcdDevice            0.01
  iManufacturer           1 ARKMICRO     
  iProduct                3 USB TO IRDA The driver ark3116 is definitely correct for your device. From *modinfo ark3116*:```
filename:       /lib/modules/3.2.0-23-generic-pae/kernel/drivers/usb/serial/ark3116.ko
description:    USB ARK3116 serial/IrDA driver
author:         Bart Hartgers <bart.hartgers+ark3116@gmail.com>
license:        GPL
srcversion:     C0BE9425652ADAF1183F01E
alias:          usb:v[COLOR="Red"]18EC[/COLOR]p[COLOR="Red"]3118[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6547p0232d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial
intree:         Y
vermagic:       3.2.0-23-generic-pae SMP mod_unload modversions 686 
parm:           debug:Enable debug (bool)
```When you operate the device; that is, push buttons on your remote, is there any recognition here:```
sudo tail -f /var/log/syslog
```You can get out of *tail* with Ctrl+c.> the IR-input device is a starting point in each and every "remote control config" HOW-TOs I see on the net. May we see a link or two?

I was looking around in Synaptic Package Manager and saw *irda-utils*. Its description is:```
This package contains userspace utilities to manage and handle infrared
devices. It includes [COLOR="Red"]irattach, findchip, irdadump[/COLOR], irdaping and irpsion5.
OBEX tools are removed since 0.9.5. If you need to use IrOBEX,
use openobex-apps package.
```I am very interested in the items I highlighted, if only to read the manual pages:```
man findchip
```It won't do me much good since I don't have such a device.

Let me just reiterate. I know nothing about such devices. I just know a bit about Linux, drivers, configuration files, et al. I love a mystery.

---

### Post by keyf on 2012-04-22
It turned out, that this particular IR controller is not for remote controllers, but just to communicate between devices (like your PC and a phone). It was a surprise for me... So it all good with the driver and settings ;)

---


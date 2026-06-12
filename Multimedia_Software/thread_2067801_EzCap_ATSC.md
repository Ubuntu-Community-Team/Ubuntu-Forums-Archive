---
title: "EzCap ATSC"
date: 2012-10-07
forum: Multimedia Software
---

### Post by daymz on 2012-10-07
I have bought this USB dongle from eBay. Labeled as EzCap ATSC. It shows up as e1ba:2875 eMPIA Technology

[B]lsusb -v

[/B]```

Bus 001 Device 002: ID eb1a:2875 eMPIA Technology, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0xeb1a eMPIA Technology, Inc.
  idProduct          0x2875 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ac  1x 940 bytes
        bInterval               1

```[B]hwinfo --usb

[/B]```
08: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: ADDn.aZuXoGqBp02
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: unknown
  Model: "eMPIA USB 2875 Device"
  Hotplug: USB
  Vendor: usb 0xeb1a "eMPIA Technology, Inc."
  Device: usb 0x2875 "USB 2875 Device"
  Revision: "1.00"
  Serial ID: "10101010"
  Driver: "em28xx"
  Driver Modules: "em28xx"
  Speed: 480 Mbps
  Module Alias: "usb:vEB1Ap2875d0100dc00dsc00dp00icFFisc00ip00"
  Driver Info #0:
    Driver Status: em28xx is active
    Driver Activation Cmd: "modprobe em28xx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #3 (Hub)

```**dmesg | grep em28xx**

```
[    5.827401] em28xx: New device  USB 2875 Device @ 480 Mbps (eb1a:2875, interface 0, class 0)
[    5.827412] em28xx: DVB interface 0 found
[    5.829355] em28xx #0: chip ID is em2874
[    6.144090] em28xx #0: found i2c device @ 0xa0 [eeprom]
[    6.188877] em28xx #0: Your board has no unique USB ID.
[    6.188891] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[    6.188899] em28xx #0: This method is not 100% failproof.
[    6.188906] em28xx #0: If the board were missdetected, please email this log to:
[    6.188914] em28xx #0:     V4L Mailing List  <linux-media@vger.kernel.org>
[    6.188921] em28xx #0: Board detected as EM2874 Leadership ISDBT
[    6.387419] em28xx #0: Identified as EM2874 Leadership ISDBT (card=77)
[    6.387432] em28xx #0: v4l2 driver version 0.1.3
[    6.482990] em28xx #0: V4L2 video device registered as video1
[    6.494508] usbcore: registered new interface driver em28xx
[    6.618558] DVB: registering new adapter (em28xx #0)
[    6.620364] em28xx #0: Successfully loaded em28xx-dvb
[    6.620376] Em28xx: Initialized (Em28xx dvb Extension) extension

```w_scan just fails with an error.

**w_scan -fa**

```
w_scan version 20111203 (compiled for DVB API 5.4)
WARNING: VDR up to version 1.7.13 doesn't support ATSC.
        Changing output format to 'vdr-1.7.x'
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
frontend_type ATSC, channellist 1
output format vdr-1.7
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
main:3079: FATAL: ***** NO USEABLE ATSC CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

```**lsmod | grep 28xx**

```

em28xx_dvb             22490  0 
dvb_core               90137  1 em28xx_dvb
em28xx                 89652  1 em28xx_dvb
v4l2_common            20569  1 em28xx
videobuf_vmalloc       13336  1 em28xx
videobuf_core          25097  2 em28xx,videobuf_vmalloc
tveeprom               17009  1 em28xx
videodev               99779  4 em28xx,v4l2_common,uvcvideo,videobuf2_core
```
The V4L2 code does include a em28xx driver, but it lists the 2875 as unknown.

Any help would be appreciated, I have ran out of options trying things.

---

### Post by oldos2er on 2012-10-07
Post moved to its own thread.

---

### Post by BicyclerBoy on 2012-10-07
Some versions of your USB gadget are supported.

[http://linuxtv.org/wiki/index.php/Easycap](http://linuxtv.org/wiki/index.php/Easycap)
[http://linuxtv.org/wiki/index.php/Em28xx_devices](http://linuxtv.org/wiki/index.php/Em28xx_devices)

Notes state some of the dongles (internal tuners) need firmware

The comments about 2874 are not very promising..

---

### Post by Bucky Ball on 2012-10-07
I have the Ezycap DVB-T and it worked out of the box.

Have you tried MeTV? It has an auto-scan function which negates the need to create your own channels.conf file (which you would then put in .xine for instance if you were using that, my personal fave).

If you have a dig you may be able to find a channels.conf for your locale online and use that.

Try booting with the Ezycap unplugged then before doing anything plug it in, open a terminal and run this:

```
dmesg
```

Do you see any action for it at the bottom of that output?

---


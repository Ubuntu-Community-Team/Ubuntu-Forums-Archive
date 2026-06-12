---
title: "Setting Acceleration for USB mouse"
date: 2010-02-18
forum: Multimedia Software
---

### Post by idsfa on 2010-02-18
I am running karmic on my lenovo T61p.

I like to use my laptop with a USB attached Logitech TrackMan Marble Wheel mouse.  Recently I noticed that the external mouse has no acceleration at all -- I have to crank on it just to move the cursor even the tiniest amount.  The touchpad and the joy-button both work fine and have normal acceleration.

I attempted to adjust the accel with both the preferences panel and xset, but neither had any effect on the USB mouse.  Unplugging and reconnecting makes no difference, nor does rebooting.

Can anyone help me get this mouse working again?

dmesg:
```
[63823.488104] usb 5-1: new low speed USB device using uhci_hcd and address 3
[63823.664338] usb 5-1: configuration #1 chosen from 1 choice
[63823.689719] input: Logitech USB-PS/2 Trackball as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input13
[63823.689905] generic-usb 0003:046D:C401.0002: input,hidraw0: USB HID v1.00 Mouse [Logitech USB-PS/2 Trackball] on usb-0000:00:1d.0-1/input0
```

Xorg.0.log
```
(II) config/hal: Adding input device Logitech USB-PS/2 Trackball
(**) Logitech USB-PS/2 Trackball: always reports core events
(**) Logitech USB-PS/2 Trackball: Device: "/dev/input/event6"
(II) Logitech USB-PS/2 Trackball: Found 3 mouse buttons
(II) Logitech USB-PS/2 Trackball: Found x and y relative axes
(II) Logitech USB-PS/2 Trackball: Found scroll wheel(s)
(II) Logitech USB-PS/2 Trackball: Configuring as mouse
(**) Logitech USB-PS/2 Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Trackball" (type: MOUSE)
(**) Logitech USB-PS/2 Trackball: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Trackball: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Trackball: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Trackball: (accel) set acceleration profile 0
(II) Logitech USB-PS/2 Trackball: initialized for relative axes.

```

lsusb -vv
```

Bus 005 Device 003: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc401 TrackMan Marble Wheel
  bcdDevice            2.10
  iManufacturer           1 Logitech
  iProduct                2 USB-PS/2 Trackball
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 38 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

```

---


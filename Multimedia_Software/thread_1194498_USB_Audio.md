---
title: "USB Audio"
date: 2009-06-22
forum: Multimedia Software
---

### Post by FlamingChainsaws on 2009-06-22
So, this laptop I'm using (Toshiba Satellite) has a big problem. The volume knob on the computer is broken off. I've tried to fix it, but I have found it to be impossible. This costs 300 dollars to fix. :(

So I'm trying to use this usb audio devie thing. It is a small thing with a headphone and microphone jack. There is no brand or model number on it, and no box...It lights up when I plug it in. I have seen, with the help of Google, that one can usually select "USB Audio" in Sound in Preferences. Unfortunately, this is not an option on here. Is there a way to enable this option? I've tried all the options that are there. Help me! I am confused!

I'm running Jaunty... :confused:

---

### Post by raboofje on 2009-06-22
Let's start by seeing if the device has been recognised by alsa: could you paste the output of 'cat /proc/asound/cards' and/or 'aplay -l'?

---

### Post by FlamingChainsaws on 2009-06-22
> **raboofje said:**
> Let's start by seeing if the device has been recognised by alsa: could you paste the output of 'cat /proc/asound/cards' and/or 'aplay -l'?
charles@charles-laptop:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 4

AND

charles@charles-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by raboofje on 2009-06-22
Ok, looks like ALSA only sees one card, which is probably your broken onboard one.

Could you paste the 'lsusb' output, and perhaps 'lsusb -v'? That should give some details about the devices currently attached to the USB bus.

---

### Post by raboofje on 2009-06-22
> **FlamingChainsaws said:**
> big problem. The volume knob on the computer is broken off. I've tried to fix it, but I have found it to be impossible.

(i'm assuming here that this is a real, physical volume knob, and not a convenient interface to control the mixer which you can also just control though software?)

---

### Post by FlamingChainsaws on 2009-06-22
charles@charles-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

AND

charles@charles-laptop:~$ lsusb -v

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x093a Pixart Imaging, Inc.
  idProduct          0x2510 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
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
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      62
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by FlamingChainsaws on 2009-06-22
> **raboofje said:**
> (i'm assuming here that this is a real, physical volume knob, and not a convenient interface to control the mixer which you can also just control though software?)
Yeah, physical knob is broken, I don't know what the deal is though.

---

### Post by raboofje on 2009-06-22
> **FlamingChainsaws said:**
> charles@charles-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Hm, and the card was plugged-in? These don't really sound like soundcards... [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids) suggests the pixart thing is an optical mouse.

---

### Post by FlamingChainsaws on 2009-06-22
> **raboofje said:**
> Hm, and the card was plugged-in? These don't really sound like soundcards (the pixart thing is more likely a webcam?)
It's plugged in as we speak, the light is on...there's no webcam...a usb mouse though.

---

### Post by raboofje on 2009-06-22
> **FlamingChainsaws said:**
> It's plugged in as we speak, the light is on...

Strange... does /var/log/messages or /var/log/syslog say anything when you plug it in and out?

---

### Post by FlamingChainsaws on 2009-06-22
Yeah, the first does - it's a lot of stuff like this:

Jun 22 19:08:47 charles-laptop kernel: [10884.348744] usb 3-1: new full speed USB device using uhci_hcd and address 22

---

### Post by raboofje on 2009-06-22
Ok, pasting a bit more of that might be useful.

---

### Post by FlamingChainsaws on 2009-06-22
Jun 22 17:47:44 charles-laptop -- MARK --
Jun 22 17:58:13 charles-laptop pulseaudio[3059]: module-rtp-send.c: Failed to push chunk into memblockq.
Jun 22 17:58:16 charles-laptop last message repeated 6 times
Jun 22 18:01:06 charles-laptop kernel: [ 6822.400093] usb 3-1: USB disconnect, address 2
Jun 22 18:01:08 charles-laptop kernel: [ 6824.526148] usb 2-1: new low speed USB device using uhci_hcd and address 2
Jun 22 18:01:08 charles-laptop kernel: [ 6824.729152] usb 2-1: configuration #1 chosen from 1 choice
Jun 22 18:01:08 charles-laptop kernel: [ 6824.859504] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input9
Jun 22 18:01:08 charles-laptop kernel: [ 6824.883015] generic-usb 0003:093A:2510.0002: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-1/input0
Jun 22 18:01:10 charles-laptop kernel: [ 6826.948066] usb 3-1: new full speed USB device using uhci_hcd and address 3
Jun 22 18:01:11 charles-laptop kernel: [ 6827.523381] usb 3-1: new full speed USB device using uhci_hcd and address 4
Jun 22 18:01:11 charles-laptop kernel: [ 6828.088064] usb 3-1: new full speed USB device using uhci_hcd and address 5
Jun 22 18:01:12 charles-laptop kernel: [ 6828.614057] usb 3-1: new full speed USB device using uhci_hcd and address 6
Jun 22 18:02:28 charles-laptop kernel: [ 6905.108425] usb 3-1: new full speed USB device using uhci_hcd and address 7
Jun 22 18:02:29 charles-laptop kernel: [ 6905.676076] usb 3-1: new full speed USB device using uhci_hcd and address 8
Jun 22 18:02:29 charles-laptop kernel: [ 6906.262558] usb 3-1: new full speed USB device using uhci_hcd and address 9
Jun 22 18:02:30 charles-laptop kernel: [ 6906.796400] usb 3-1: new full speed USB device using uhci_hcd and address 10
Jun 22 18:27:44 charles-laptop -- MARK --
Jun 22 18:47:44 charles-laptop -- MARK --
Jun 22 18:52:01 charles-laptop kernel: [ 9878.049262] usb 3-1: new full speed USB device using uhci_hcd and address 11
Jun 22 18:52:02 charles-laptop kernel: [ 9878.622688] usb 3-1: new full speed USB device using uhci_hcd and address 12
Jun 22 18:52:02 charles-laptop kernel: [ 9879.188069] usb 3-1: new full speed USB device using uhci_hcd and address 13
Jun 22 18:52:03 charles-laptop kernel: [ 9879.716083] usb 3-1: new full speed USB device using uhci_hcd and address 14
Jun 22 18:52:24 charles-laptop kernel: [ 9900.764374] usb 3-1: new full speed USB device using uhci_hcd and address 15
Jun 22 18:52:24 charles-laptop kernel: [ 9901.336071] usb 3-1: new full speed USB device using uhci_hcd and address 16
Jun 22 18:52:25 charles-laptop kernel: [ 9901.908521] usb 3-1: new full speed USB device using uhci_hcd and address 17
Jun 22 18:52:26 charles-laptop kernel: [ 9902.436073] usb 3-1: new full speed USB device using uhci_hcd and address 18
Jun 22 19:07:44 charles-laptop -- MARK --
Jun 22 19:08:46 charles-laptop kernel: [10882.692089] usb 3-1: new full speed USB device using uhci_hcd and address 19
Jun 22 19:08:46 charles-laptop kernel: [10883.260089] usb 3-1: new full speed USB device using uhci_hcd and address 20
Jun 22 19:08:47 charles-laptop kernel: [10883.821031] usb 3-1: new full speed USB device using uhci_hcd and address 21
Jun 22 19:08:47 charles-laptop kernel: [10884.348744] usb 3-1: new full speed USB device using uhci_hcd and address 22
Jun 22 19:27:44 charles-laptop -- MARK --

---

### Post by raboofje on 2009-06-22
Well, beats me. Anyone else? :)

---

### Post by FlamingChainsaws on 2009-06-22
I'm gonna stab myself in the face.

---


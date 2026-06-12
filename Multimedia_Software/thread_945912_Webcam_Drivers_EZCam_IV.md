---
title: "Webcam Drivers EZCam IV"
date: 2008-10-12
forum: Multimedia Software
---

### Post by leonox on 2008-10-12
Hi, I just got two webcams EZonic EZCam IV, I have used them without problems under Windows XP and Vista, now I want to use one of them in a Linux (Ubuntu) box. I googled and I didn't find a lot, I just found drivers for the EZCam III and a [_page_]("http://http://www.qbik.ch/usb/devices/showdev.php?id=4303") that if I understood [_sells_]("http://http://www.linux-projects.org/downloads/sn9cxxx-unlimited.html") the drivers for the webcam... but I want it for free.

I tried them with Cheese and all I see is a black screen.

I executed dmesg and got the following output...

```

[93506.076333] usb 1-2: new full speed USB device using uhci_hcd and address 2
[93506.241052] usb 1-2: configuration #1 chosen from 1 choice
[93506.573377] Linux video capture interface: v2.00
[93506.639688] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
[93506.640894] usb 1-2: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613C)
[93506.749593] usb 1-2: No supported image sensor detected for this bridge
[93506.749634] usbcore: registered new interface driver sn9c102
[93506.787111] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
[93506.788574] usbcore: registered new interface driver gspca

```

If I understand Ubuntu detected the webcam... but it's not working very well... how can I solve this problem? do I have to wait for someone to write a driver? or how can I write one? I'm in the disposition to learn to write linux drivers (I'm a computer science student)

What is GSPCA?

I found the guy that wrote the EZCam III driver... just some links about him..

[http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams]("http://www.theinquirer.net/en/inquirer/news/2007/04/30/one-man-writes-linux-drivers-for-235-usb-webcams")
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")
[http://mxhaard.free.fr/sview.html]("http://mxhaard.free.fr/sview.html")

I hope that someone can give me some help or guidance... :KS

---

### Post by leonox on 2008-10-13
For one moment I had a hope... I found a guy that said he made the same camera work under linux and using Cheese!!!... but then he realized that he was using another model, anyway I followed his recommendation, but it didn't help a lot.	:-(

[http://encephalosponge.com/2008/05/21/say-cheese/]("http://encephalosponge.com/2008/05/21/say-cheese/")

---

### Post by leonox on 2008-10-13
More info about the webcam...

```
$ sudo lsusb -v -s 1:5

Bus 001 Device 005: ID 0c45:613c Microdia 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0c45 Microdia
  idProduct          0x613c 
  bcdDevice            1.01
  iManufacturer           0 
  iProduct                1 USB camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          279
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x02a8  1x 680 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0320  1x 800 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0384  1x 900 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       8
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             100
Device Status:     0x0000
  (Bus Powered)


```

---

### Post by jblackhall on 2008-10-13
Hi, I'm Jonathan, the guy from encephalosponge.com.  It turns out, we have the same Device ID, so it's essentially the same camera.  Are you running Hardy?  My output on Cheese looks pretty dark right now too, but it's actually detecting the video.  Try pointing the camera directly at a light and see if you get any picture in Cheese.  Have you tried Ekiga?  That's where I use it most of the time, and it works fine there.  Try setting it up as a v4l camera with Ekiga (and make sure you're in video mode with the camera button pressed).  Also, if you're seeing a black screen in Cheese, that most likely means it's detecting your camera.  If it didn't, you'd see a screen with colored lines and static.  Now as far as how to fix Cheese to display correctly, that's a different story.  I'm not entirely sure how to do that.

BUT, I just tried Cheese and the picture was incredibly dark.  Then I tried Ekiga, and it was nice and bright (after a few seconds warm up).  Now I tried Cheese again and it looks much better.  Not quite sure why that would be.  You might try filing a bug report about it or see if there's one available.

---

### Post by jblackhall on 2008-10-13
also, you were wondering what GSPCA is.  I found a [nice video]("http://www.linuxjournal.com/video/get-your-webcam-working-gspca") that explains things fairly well, but I would not recommend mucking around in the Terminal too much if you're not sure what you're doing.  You could definitely screw some things up and the commands can be fairly confusing if you're not used to them.  If you decide you want to play around, you shouldn't need to compile/install gspca itself.  if you run the following command, you should be able to verify that it's installed:
```
lsmod | head -n 6
```
My output:
```
jonathan@jonathan-ubuntu:~$ lsmod | head -n 6
Module                  Size  Used by
sn9c102               134148  0 
gspca                 657872  0 
compat_ioctl32         11136  2 sn9c102,gspca
videodev               30720  2 sn9c102,gspca
v4l2_common            21888  3 sn9c102,compat_ioctl32,videodev

```

The second half of that video will probably be much more useful to you, as you can use it to adjust the default brightness to your camera (at the kernel module level).  Like I said, if you're not comfortable screwing around in Terminal, don't do it.  Surely there has to be a better answer for this, hopefully coming up in Intrepid.  I know there's a guy at Fedora working very hard to [improve webcam support]("http://fedoraproject.org/wiki/Features/BetterWebcamSupport") for Linux and his stuff will carry over to Ubuntu, no doubt.

I'm not linux expert, but feel free to ask questions.  I'll try to help if I'm able.

---


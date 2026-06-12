---
title: "Creative Webcam Live"
date: 2008-04-26
forum: Multimedia Software
---

### Post by keithcleaver on 2008-04-26
Hi guys.

I'm trying to get my Creative Webcam Live! working. I've read the other thread about a similar camera, and followied the instructions there as best as I can, but to no avail. here's my lsusb output, as suggested in the other thread:

```

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Bus 001 Device 001: ID 0000:0000

```

Any help with this would be appreciated, as this is the only thing preventing me from dumping windoze for good.

---

### Post by Shannon_VanWagner on 2008-05-21
This webcam (Creative VF-0050) is working great for me on Ubuntu 8.04, using the "cheese" webcam util.

From sudo lsusb -v
---------------------------------------------------------------------------------
Bus 001 Device 005: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x4036 Webcam Live!/Live! Pro
  bcdDevice            1.00
  iManufacturer           1 Creative Labs  
  iProduct                2 WebCam Live!   
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          193
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              160mA
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
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
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           2
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           2
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           2
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
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           2
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
---------------------------------------------------------------------------------

What program are you using to test the webcam?
Does the light on the webcam turn on?
Have you tried any of the programs below to test the webcam?
kopete, amsn, cheese, camorama, ekiga, v4l-conf

Have you tried to cat /dev/video0 and then push CTRL+C to stop the command (you should see a bunch of gobblygook(binary output))?

Have you run the command v4l-info(must sudo apt-get install v4l-conf first)?

---

### Post by Shannon_VanWagner on 2008-05-21
Here's a few more utilities to try:
- xawtv: the canonical video4linux test application
- camstream
- effectv
- Motion
- Wengophone

---

### Post by pearsonapollo on 2008-05-21
I am having the same problem with my Creative Notebook Ultra.  When I issue the lsusb command I get
 *Bus 002 Device 009: ID 041e:403d Creative Technology, Ltd WebCam Notebook Ultra*

I have installed Xawtv, Cheese and Camorama.  When I load Camorama I get 
*Could not connect to video device [I]/dev/video0*  

Do I need to manually mount the web cam?

Also, I did a sudo apt-get install vl4-conf and I got this during installation [I]Adding system user `motion' (UID 112) ...
Adding new user `motion' (UID 112) with group `motion' ...
Not creating home directory `/home/motion'.
Starting motion detection : motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3352064 LIBAVFORMAT_BUILD 3344896
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] Failed to open video device /dev/video0: No such file or directory
[1] Capture error calling vid_start
[1] Thread finishing...
.

Processing triggers for libc6 ...
[/I]

I am running Hardy 8.04 LTS.  Thank you all for any help in advance.

---

### Post by VHans on 2008-05-26
I am also having trouble with a Creative Labs Webcam Live! Ultra.

When I run xawtv I get following error:

```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.24-16-generic)
xinerama 0: 1280x1024+1600+0
xinerama 1: 1600x1200+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Bestand of map bestaat niet
v4l2: open /dev/video0: Bestand of map bestaat niet
v4l: open /dev/video0: Bestand of map bestaat niet
no video grabber device available

```

---

### Post by Roger D on 2008-05-27
If your camera is uvc compatible, it ought to work with Hardy. Check for compatibility at [http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices).

I've got a uvc compatible camera - a Logitech Quickcam Pro 9000, but have had lots of problems  - still can't get Cheese to work. However, I can now record video and sound using guvcview. You can download this from: [http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666](http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666)

It's well worth trying.

Roger D

---

### Post by VHans on 2008-05-28
> **Roger D said:**
> If your camera is uvc compatible, it ought to work with Hardy. Check for compatibility at [http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices).

I've got a uvc compatible camera - a Logitech Quickcam Pro 9000, but have had lots of problems  - still can't get Cheese to work. However, I can now record video and sound using guvcview. You can download this from: [http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666](http://developer.berlios.de/project/showfiles.php?group_id=8179&release_id=14666)

It's well worth trying.

Roger D

Does it work on 64bit? I get a 'wrong architecture' message when opening the file.

---

### Post by Roger D on 2008-05-28
Sorry, I don't know. I'm 32 bit

---

### Post by 11hjpphty76lkjj on 2008-05-31
I used the process here:

[http://forum.eeeuser.com/viewtopic.php?id=26570](http://forum.eeeuser.com/viewtopic.php?id=26570)

1. sudo aptitude install subversion
2. svn co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
3. cd linux-uvc
4. sudo make
5. sudo make install
6. sudo modprobe -r uvcvideo
7. sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
8. sudo cp uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko
9. sudo modprobe uvcvideo

and it worked for me.

A

---


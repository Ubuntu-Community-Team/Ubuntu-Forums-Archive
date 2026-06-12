---
title: "Freecom DVB-T"
date: 2008-06-08
forum: Multimedia Software
---

### Post by groeswenphil on 2008-06-08
Thought you'd like to know that this product, the Freecom DVB-T USB television doohdad
[http://www.freecom.com/ecproduct_detail.asp?id=2234](http://www.freecom.com/ecproduct_detail.asp?id=2234)

Works flawlessly in Hardy Heron.
Works with ME TV

Instantly....no fuss....just works.

Phil

---

### Post by Gina on 2008-06-10
I've recently bought one of those very things and searched the forums for info.  Your post came out of the search.  YIPPEE I thought - it should work :)  Well it doesn't :(  So, wondering if it was faulty hardware I ran up the "legacy" Win XP which I still have available on one PC, installed driver and software for it and that worked - in fact very well.  Unfortunately not much help for my AMD 64 system which only has Ubuntu.

I believe you must have something installed that I don't as I've just tried the device on my P4 (the one with Windoze) under Hardy 32 bit and exactly the same hardware and still get "No tuner device" error in Me TV.  Any ideas, please?

---

### Post by groeswenphil on 2008-06-10
As far as I remember, this is what I did.
I'm running Ubuntu Hardy AMD 64.
I plugged the doohdad in.
Nothing happened.
Did some searching and it looked like I needed some software.
First I downloaded Kaffein.
It didn't work, but it looked as though it might if I fiddled.
Then I added ME Tv.
It started up and asked me to pick my local transmiter from a huge list....worldwide.
Mine was on the list so I picked it.
It thought about things for a while as it loaded channel information....then it started.
Perfect picture on main channels....some of the more exotic ones break up.

So........try adding kaffein and ME TV.....and I think they were both available through Synaptic.

Tell me how you get on.
Phil

---

### Post by Gina on 2008-06-10
OK did that - even installed a new AMD64 Hardy in a new partition and ran all the updates - same result "No tuner device" error at Me TV startup.  Tried Kaffeine too - no sign of a tuner device :(  I think you must have installed something else or changed a setting somewhere - unless there's some obscure fault with my PC.

Thank you for any help you can give :)

---

### Post by groeswenphil on 2008-06-10
What sort of graphics card have you got?
I've got Nvidia.
The only other thing that I can think of is that either
a) I got lucky.........or 
b) I've installed something else that makes the doohdad work.
You got Real Player?
What happens when you launch ME Tv?

Phil

---

### Post by groeswenphil on 2008-06-10
Just took a look at Kaffein..........which has an awful lot of buttons and knobs and settings that you can twiddle with.....and they have a forum.

[https://answers.launchpad.net/ubuntu/hardy/+source/kaffeine/+questions](https://answers.launchpad.net/ubuntu/hardy/+source/kaffeine/+questions)

Have you tried the doohdad in a different slot?
Phil

---

### Post by Gina on 2008-06-10
> **groeswenphil said:**
> What sort of graphics card have you got?
I've got Nvidia.
The only other thing that I can think of is that either
a) I got lucky.........or 
b) I've installed something else that makes the doohdad work.
You got Real Player?
What happens when you launch ME Tv?

PhilOnboard Nvidia® Geforce 6100GS graphics supporting up to 256MB 
Haven't installed RealPlayer
Starting Me TV gives error popup "No tuner device" - then no option but to click OK which removes the error box and shuts down Me TV> **groeswenphil said:**
> Just took a look at Kaffein..........which has an awful lot of buttons and knobs and settings that you can twiddle with.....and they have a forum.

[https://answers.launchpad.net/ubuntu/hardy/+source/kaffeine/+questions](https://answers.launchpad.net/ubuntu/hardy/+source/kaffeine/+questions)

Have you tried the doohdad in a different slot?
PhilI'll check out that Kaffeine stuff tomorrow
I've tried various USB slots - on rear (mobo), front USB connected to mobo header and USB PCI card - all USB2 - no difference.

I dug out my old DVB-T tuner unit (large, separate power supply and not very sensitive) and that still works with Kaffeine.  Me TV doesn't have our local transmitter in the list (Stockland Hill).  I made my own for Kaffeine a while back using another Kaffeine multiplex list edited with data for our local area obtained from website.

Strange that Kaffeine recognises my old TV tuner but not the Freecom - yet both work in Win XP.

The quote in your sig is very apt! ;)

---

### Post by Gina on 2008-06-11
I've been trying the suggested things in the Kaffeine section of launchpad (Kaffeine cannot find DVB)...  This id the appropriate section of the result of lsusb -v> Bus 001 Device 003: ID 14aa:0160 AVerMedia (again) or C&E 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x14aa AVerMedia (again) or C&E
  idProduct          0x0160 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              6 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ac  1x 940 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
And this is for the old Hauppauge box > Bus 003 Device 003: ID 0b48:1005 TechnoTrend AG Technotrend/Hauppauge USB-Nova
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0b48 TechnoTrend AG
  idProduct          0x1005 Technotrend/Hauppauge USB-Nova
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          415
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0390  1x 912 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0360  1x 864 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0

I think at this point I'm out of my depth!

---

### Post by groeswenphil on 2008-06-11
Actually, I worked my way through all of that ..........and I ended up with an Aran sweater.

Might be best if you pop around to my place when you want to watch TV   :O)

Bet you get it to work in the end.
Phil

---

### Post by Gina on 2008-06-11
Well... I suppose South Wales isn't SO far to go from here :lolflag:

It's good to know someone has got it working anyway :)

---

### Post by Gina on 2008-06-12
Been doing some research and it seems the Freecom unit now uses a different chipset - maybe yours used the older one.  The ID of mine is **14aa:0160** so this quote seems to apply>   [B]Freecom rev 4 DVB-T USB 2.0 tuner
[/B]
The latest Freecom/Yacumo usb stick has a Realtek 2831U chipset and any of the following usb id's: **14aa:0160**, 0bda:2831, 2304:022b, 185b:0100, 13d3:3216, 13d3:3220, 13d3:3236, 13d3:3244, 08dd:2103. Latest Windows drivers dates january 2007 and can be downloaded at freecom.com If anyone has any info on how to get these to work or if a specific firmware works, please add it here.

Chipset info at [http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=35&Level=4&Conn=3&ProdID=147](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=35&Level=4&Conn=3&ProdID=147)

UPDATE: Realtek submitted a v0.0.2 of their driver feb 20th 2008. This has been confirmed to function for this Freecom (or Conceptronic) stick with usb id: 14aa:0160 on a 2.6.22.17 kernel. This stick has a MT2061F tuner chip, but this driver also supports the MLX5005 tuner chip. No additional firmware file is needed.

The driver source can be downloaded from [[91]]("http://www.megaupload.com/?d=DPE2C8I5"), but be aware it has only be confirmed to work on devices with usb id 14aa:0160.

For easier installation you can use [[92]]("http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.2mod.tar.gz"). Just unpack and do a make and sudo make install.So I'll have a go with that.  I don't have the particular kernel mentioned but I'm hoping later ones will work (ie. the Hardy one).

---

### Post by Gina on 2008-06-14
Well it "makes" and installs without error - but still the device won't work :(

---


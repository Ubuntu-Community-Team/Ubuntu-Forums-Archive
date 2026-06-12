---
title: "PixelView PlayTV 405 DVD Maker"
date: 2008-05-28
forum: Multimedia Software
---

### Post by lnunes.eng on 2008-05-28
Hi all!

I have a PixelView USB card, trying to put this to work on 7.10...

The comand "lsusb -v" shows me:

---------------------------------------------------------------------

Bus 005 Device 007: ID 6000:0001  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x6000 
  idProduct          0x0001 
  bcdDevice            0.01
  **iManufacturer          16 Trident**
  iProduct               32 TVBOX
  iSerial                64 2004090820040908
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         48 2.0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
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
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled
---------------------------------------------------------------------

I tried:

[http://tiagovaz.wordpress.com/2007/11/24/pixelview-play-tv-405-dvd-makerusb-tv-tuner/](http://tiagovaz.wordpress.com/2007/11/24/pixelview-play-tv-405-dvd-makerusb-tv-tuner/)
(this is the same model as mine)

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

All this stop on tm6000 modules (don't know if this is the correct module), all times I try to compile this module, I got the error:

-----------------------------------------------------------------------
root@nunes:~/temp/v4l-dvb/v4l# modprobe tm6000 
FATAL: Error inserting tm6000 (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/tm6000/tm6000.ko): Unknown symbol in module, or unknown parameter (see dmesg)
-----------------------------------------------------------------------

dmesg output is:

-----------------------------------------------------------------------
[ 1310.464000] Linux video capture interface: v2.00
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_streamoff
[ 1310.484000] tm6000: Unknown symbol videobuf_streamoff
[ 1310.484000] tm6000: disagrees about version of symbol dvb_dmxdev_init
[ 1310.484000] tm6000: Unknown symbol dvb_dmxdev_init
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_poll_stream
[ 1310.484000] tm6000: Unknown symbol videobuf_poll_stream
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_reqbufs
[ 1310.484000] tm6000: Unknown symbol videobuf_reqbufs
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_waiton
[ 1310.484000] tm6000: Unknown symbol videobuf_waiton
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_dqbuf
[ 1310.484000] tm6000: Unknown symbol videobuf_dqbuf
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_to_vmalloc
[ 1310.484000] tm6000: Unknown symbol videobuf_to_vmalloc
[ 1310.484000] tm6000: disagrees about version of symbol dvb_register_adapter
[ 1310.484000] tm6000: Unknown symbol dvb_register_adapter
[ 1310.484000] tm6000: disagrees about version of symbol videobuf_vmalloc_free
[ 1310.484000] tm6000: Unknown symbol videobuf_vmalloc_free
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_read_stream
[ 1310.488000] tm6000: Unknown symbol videobuf_read_stream
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_querybuf
[ 1310.488000] tm6000: Unknown symbol videobuf_querybuf
[ 1310.488000] tm6000: disagrees about version of symbol video_unregister_device
[ 1310.488000] tm6000: Unknown symbol video_unregister_device
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_qbuf
[ 1310.488000] tm6000: Unknown symbol videobuf_qbuf
[ 1310.488000] tm6000: disagrees about version of symbol dvb_dmxdev_release
[ 1310.488000] tm6000: Unknown symbol dvb_dmxdev_release
[ 1310.488000] tm6000: disagrees about version of symbol video_device_alloc
[ 1310.488000] tm6000: Unknown symbol video_device_alloc
[ 1310.488000] tm6000: disagrees about version of symbol video_register_device
[ 1310.488000] tm6000: Unknown symbol video_register_device
[ 1310.488000] tm6000: disagrees about version of symbol dvb_frontend_detach
[ 1310.488000] tm6000: Unknown symbol dvb_frontend_detach
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_iolock
[ 1310.488000] tm6000: Unknown symbol videobuf_iolock
[ 1310.488000] tm6000: disagrees about version of symbol dvb_unregister_frontend
[ 1310.488000] tm6000: Unknown symbol dvb_unregister_frontend
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_streamon
[ 1310.488000] tm6000: Unknown symbol videobuf_streamon
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_queue_vmalloc_init
[ 1310.488000] tm6000: Unknown symbol videobuf_queue_vmalloc_init
[ 1310.488000] tm6000: disagrees about version of symbol dvb_register_frontend
[ 1310.488000] tm6000: Unknown symbol dvb_register_frontend
[ 1310.488000] tm6000: disagrees about version of symbol video_device_release
[ 1310.488000] tm6000: Unknown symbol video_device_release
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_mmap_mapper
[ 1310.488000] tm6000: Unknown symbol videobuf_mmap_mapper
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_cgmbuf
[ 1310.488000] tm6000: Unknown symbol videobuf_cgmbuf
[ 1310.488000] tm6000: disagrees about version of symbol videobuf_mmap_free
[ 1310.488000] tm6000: Unknown symbol videobuf_mmap_free
[ 1489.912000] tm6000: disagrees about version of symbol videobuf_streamoff
[ 1489.912000] tm6000: Unknown symbol videobuf_streamoff
[ 1489.912000] tm6000: disagrees about version of symbol dvb_dmxdev_init
[ 1489.912000] tm6000: Unknown symbol dvb_dmxdev_init
[ 1489.912000] tm6000: disagrees about version of symbol videobuf_poll_stream
[ 1489.912000] tm6000: Unknown symbol videobuf_poll_stream
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_reqbufs
[ 1489.916000] tm6000: Unknown symbol videobuf_reqbufs
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_waiton
[ 1489.916000] tm6000: Unknown symbol videobuf_waiton
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_dqbuf
[ 1489.916000] tm6000: Unknown symbol videobuf_dqbuf
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_to_vmalloc
[ 1489.916000] tm6000: Unknown symbol videobuf_to_vmalloc
[ 1489.916000] tm6000: disagrees about version of symbol dvb_register_adapter
[ 1489.916000] tm6000: Unknown symbol dvb_register_adapter
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_vmalloc_free
[ 1489.916000] tm6000: Unknown symbol videobuf_vmalloc_free
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_read_stream
[ 1489.916000] tm6000: Unknown symbol videobuf_read_stream
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_querybuf
[ 1489.916000] tm6000: Unknown symbol videobuf_querybuf
[ 1489.916000] tm6000: disagrees about version of symbol video_unregister_device
[ 1489.916000] tm6000: Unknown symbol video_unregister_device
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_qbuf
[ 1489.916000] tm6000: Unknown symbol videobuf_qbuf
[ 1489.916000] tm6000: disagrees about version of symbol dvb_dmxdev_release
[ 1489.916000] tm6000: Unknown symbol dvb_dmxdev_release
[ 1489.916000] tm6000: disagrees about version of symbol video_device_alloc
[ 1489.916000] tm6000: Unknown symbol video_device_alloc
[ 1489.916000] tm6000: disagrees about version of symbol video_register_device
[ 1489.916000] tm6000: Unknown symbol video_register_device
[ 1489.916000] tm6000: disagrees about version of symbol dvb_frontend_detach
[ 1489.916000] tm6000: Unknown symbol dvb_frontend_detach
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_iolock
[ 1489.916000] tm6000: Unknown symbol videobuf_iolock
[ 1489.916000] tm6000: disagrees about version of symbol dvb_unregister_frontend
[ 1489.916000] tm6000: Unknown symbol dvb_unregister_frontend
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_streamon
[ 1489.916000] tm6000: Unknown symbol videobuf_streamon
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_queue_vmalloc_init
[ 1489.916000] tm6000: Unknown symbol videobuf_queue_vmalloc_init
[ 1489.916000] tm6000: disagrees about version of symbol dvb_register_frontend
[ 1489.916000] tm6000: Unknown symbol dvb_register_frontend
[ 1489.916000] tm6000: disagrees about version of symbol video_device_release
[ 1489.916000] tm6000: Unknown symbol video_device_release
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_mmap_mapper
[ 1489.916000] tm6000: Unknown symbol videobuf_mmap_mapper
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_cgmbuf
[ 1489.916000] tm6000: Unknown symbol videobuf_cgmbuf
[ 1489.916000] tm6000: disagrees about version of symbol videobuf_mmap_free
[ 1489.916000] tm6000: Unknown symbol videobuf_mmap_free
---------------------------------------------------------------------

Someone have this card? Someone get this working?:confused:

Is there any other information I can put here to help somebody to help me?

Or there is a How-To that I didn't find? :(

Thanks in advance.... adn Help, please!

---

### Post by lnunes.eng on 2008-05-29
Anybody? :confused:

---


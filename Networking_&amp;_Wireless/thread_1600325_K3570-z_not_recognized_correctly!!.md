---
title: "K3570-z not recognized correctly??!!"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by polopete on 2010-10-18
device 
Vodafone /ZTE K3570-z

i have been booting from windows into ubuntu 9.04 so many times trying to install things and dependencies and have finally got the Vodafone / betavine software installed,  the problem i'm having is the system still doesn't recognize my mobile broadband dongle at all,  i have done a lsusb and it shows the vendor and product id but shows no name,  i hoping this is the problem and it is solvable.  
supplying lsusb and lsusb -v of the device

home@ubuntu:~$ lsusb
Bus 001 Device 006: ID 19d2:1007  
Bus 001 Device 005: ID 3538:0059 Power Quotient International Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Bus 001 Device 006: ID 19d2:1007  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x19d2 
  idProduct          0x1007 
  bcdDevice            0.00
  iManufacturer           2 Vodafone (ZTE)
  iProduct                1 Vodafone Mobile Broadband K3570-Z
  iSerial                 3 P680A8VDFD000000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

---

### Post by pdc on 2010-10-19
9.04 is now 18months old; so not supported I suspect;
if you want to go on using it, can I suggest you download this small programme: sakis3g

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation)

this page gives ubuntu instructions: it is only 200k I think, so quick;

I used it on Vodafone UK and Vodafone NL this year; it worked well;

this is the home page: [http://www.sakis3g.org/](http://www.sakis3g.org/)

it has:

list of providers and usb_modeswitch built in, so it just .. works

---

### Post by polopete on 2010-10-20
thank you pdc,  that worked a treat.  Sorry for posting about a now unsupported distro but i keep getting the same problem with later version's of Ubuntu and mint9 which just keep freezing the system.

---

### Post by pdc on 2010-10-20
well done! You did very well to get that up and running so quickly; sakis will be pleased!

[http://forum.sakis3g.org/smf/index.php](http://forum.sakis3g.org/smf/index.php)

use what works for you !!

OH: if you can mark your subject as SOLVED; that looks good for posterity!

---

### Post by inetpro on 2010-11-27
With a tip from the [Betavine forum]("http://www.betavine.net/bvportal/forums/index.html?threadId=ff8080812988fa9c012a3ca78fc002ac&postId=ff8080812988fa9c012a3ca78fc002ad") I got the K3570-Z working on both Kubuntu Lucid and Kubuntu Meerkat as follows:

```

$ sudo aptitude install python-twisted-core python-tz python-gnomekeyring python-notify wmctrl network-manager-gnome python-glade2 python-gnome2
$ mkdir VC
$ cd VC
$ wget https://forge.betavine.net/frs/download.php/654/bcm_2.99.12-1_all.deb
$ wget https://forge.betavine.net/frs/download.php/652/python-messaging_0.5.9-1_all.deb
$ wget https://forge.betavine.net/frs/download.php/651/usb-modeswitch-data_20100826-1betavine1_all.deb
$ wget https://forge.betavine.net/frs/download.php/653/wader-core_0.5.5-1_all.deb
$ sudo dpkg -i *.deb

```

**UPDATE**:
After installing the above I was able to add a new Mobile Broadband connection and connect with the standard KDE network manager found in Kubuntu 10.04 as well as on my Kubuntu 10.10 Netbook.

---


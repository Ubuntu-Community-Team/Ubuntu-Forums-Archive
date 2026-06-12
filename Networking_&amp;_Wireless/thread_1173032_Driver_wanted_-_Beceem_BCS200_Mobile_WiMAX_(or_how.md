---
title: "Driver wanted - Beceem BCS200 Mobile WiMAX (or how to heck with ndiswrapper)"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by zongpog on 2009-05-29
Dear all,

    I am looking for a driver for this USB Wimax card I bought. It came
with a subscription for a WiMax company in Holland called aerea.nl.  
The USB casing has written on it:  Alcatel-Lucent 9799 MIMO USB
Dongle, 3.5Mhz, P/N: 1AF16115ABAA However, the o/p of lsusb -v shows
that this is actually a USB device made by Beceem.

The kernel on my laptop is 2.6.28-11-generic Ubuntu i686

I installed the s/w that came with the card with WINE.  Its a connection
manager and the GUI installs and runs. Of course, it does not pick up the
card.  These USB drivers come with the card, and the ones that relate to the hardware ID are :

~/.wine/drive_c/Program Files/Alcatel-Lucent/WCM/Driver/USB# ls -1
bcmbusctr.cat
BcmBusCtr.inf
BcmBusCtr.sys

I have loaded the BcmBusCtr into NDISwrapper but do not know how to test that it might work.
# /usr/sbin/ndiswrapper -l
bcmbusctr : driver installed
Note that I think this ought to say driver installed, hardware present.

The other drivers that came with the s/w are here. 
drxvi314.cat
drxvi314.inf
drxvi314.sys
macxvi200.bin
macxvi.cfg
(I tried to load the drxvi314 just in case, but got invalud driver error or something.)


Does anyone know of anyway of getting this to run on Linux?

Regards, Z.

```

# lsusb -v
Bus 002 Device 008: ID 198f:0210 Beceem Communications Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x198f Beceem Communications Inc.
  idProduct          0x0210
  bcdDevice            0.01
  iManufacturer           1 Beceem Communications
  iProduct                2 BCS200 Mobile WiMAX
  iSerial                 3 N/A
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          111
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
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)


```

---

### Post by nayoooo on 2009-07-02
I had the same problem , does anyone hear our scream ??

---

### Post by zongpog on 2009-07-03
Nope :(

I spoek with Beecam and they said that although there were some Linux binaries these were for internal use only.  The next release of their WiMAx USB card will have Linux drivers.  This does not help us.

---

### Post by libyan.ldn on 2009-08-26
> **nayoooo said:**
> I had the same problem , does anyone hear our scream ??
i hear you scream but no hope from this company we must work on 
[I][I]reverse engineer 
to build our driver ok 
good luck for you and me 

[/I][/I]

---

### Post by alSee on 2009-09-28
Russia's Comstar Wimax provider sells the same adapter for its network. 
So who will open a project for the driver development (similar to MadWimax)?

---

### Post by Israeru on 2010-07-13
Hi

In the internet i found two sites with some data about the Beceem linux driver:

[http://wireless80211.wordpress.com/2009/11/15/beceem-wimax-on-2-6-30/](http://wireless80211.wordpress.com/2009/11/15/beceem-wimax-on-2-6-30/)

and

[http://groups.google.com/group/wimax-hacking/browse_thread/thread/5e4a667cb915f584?pli=1](http://groups.google.com/group/wimax-hacking/browse_thread/thread/5e4a667cb915f584?pli=1)

In the second link they put a file with the source code for a linux used in an access point by Motorola and the source code for the Beceem driver (that thing uses the Beceem chipset) 

I use Mandriva and I tried to compile in my distro but seems that I dont have all the headers required:

root@localhost Source]# make
make -Wall ARCH=x86 -C /lib/modules/2.6.31.13-server-1mnb/build  SUBDIRS=/home/israel/Beceem/Source/Driver/Source modules
make[1]: se ingresa al directorio `/usr/src/linux-2.6.31.13-server-1mnb'
  CC [M]  /home/israel/Beceem/Source/Driver/Source/Arp.o
En el fichero incluído de /home/israel/Beceem/Source/Driver/Source/Arp.c:21:
/home/israel/Beceem/Source/Driver/Source/Headers.h:66:39: error: asm/avalanche/generic/pal.h: No existe el fichero o el directorio
En el fichero incluído de /home/israel/Beceem/Source/Driver/Source/Headers.h:78,
                 de /home/israel/Beceem/Source/Driver/Source/Arp.c:21:
/home/israel/Beceem/Source/Driver/Source/Adapter.h:28:27: error: asm/semaphore.h: No existe el fichero o el directorio
/home/israel/Beceem/Source/Driver/Source/Arp.c: En la función ‘reply_to_arp_request’:
/home/israel/Beceem/Source/Driver/Source/Arp.c:54: error: ‘struct net_device’ no tiene un miembro llamado ‘priv’
make[2]: *** [/home/israel/Beceem/Source/Driver/Source/Arp.o] Error 1
make[1]: *** [_module_/home/israel/Beceem/Source/Driver/Source] Error 2
make[1]: se sale del directorio `/usr/src/linux-2.6.31.13-server-1mnb'
make: *** [default] Error 2

Try to compile it.

If you can I am going to test the driver, I have one modem from Yota Scartel that use the Beceem chipset.

Greetings

---

### Post by randi2kewl on 2011-09-11
Any resolution to this issue?

---

### Post by pdc on 2011-09-11
If you google on this 

linux Beceem BCS200 Mobile WiMAX

you find that is like so many of these devices: it needs switching to be seen as a modem;

...that now seems addressed in usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4945&sid=516468147537950c398674c3e8dd7825](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4945&sid=516468147537950c398674c3e8dd7825)

this post says if you plug the device in to a usb port and type

> lsusb

 in a terminal; if you see

> "198f:0220", then your device is in the right mode already. It was switched automatically.

the last couple of posts in the above thread;

give advice on how to build a driver; as a kernel module;

so it seems to me: you need two things

1) usb_modeswitch
2) driver in the kernel

and this link

[http://cateee.net/lkddb/web-lkddb/BCM_WIMAX.html](http://cateee.net/lkddb/web-lkddb/BCM_WIMAX.html)

is quoted by Josh in the above thread; the driver bcm is coming soon; and can be built if you so wish..................

---

### Post by Israeru on 2011-10-18
In the internets exist a project to use the driver from Sprint in ubuntus 10.04 [http://code.google.com/p/bcm-wimax/](http://code.google.com/p/bcm-wimax/)

I tried it but the modem only blink the ligths two times and dont create the eth1 interface. 

Can you try this?:popcorn:

---

### Post by richman1000000 on 2011-11-20
[http://www.opennet.ru/tips/info/2468.shtml#1](http://www.opennet.ru/tips/info/2468.shtml#1) - full information  [http://code.google.com/p/beceem-wimax/](http://code.google.com/p/beceem-wimax/) - my project of kernel module driver but unlike [http://code.google.com/p/bcm-wimax/](http://code.google.com/p/bcm-wimax/) I patched it for 2.6.xx linux kernels and checked my installer

---


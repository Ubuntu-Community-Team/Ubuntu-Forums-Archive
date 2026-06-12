---
title: "Setting up wireless"
date: 2013-08-14
forum: Networking &amp; Wireless
---

### Post by Bill_Sutton on 2013-08-14
have a Belkin ac1200 modem / router and want to connect to it by wireless

Have the ac wi=fi dual-band USB adapter and would like to know how to set it up with Ubuntu? Have read that some brands/models have problems with Ubuntu so thought I would ask first.
 
At the moment I have a very long cable that is getting in the way so thats the main reason for going wireless

edit: looked at the wiki and the model is not mentioned, Model Number is :F9L1106v1

---

### Post by carl4926 on 2013-08-14
We need to know what chip it has

In a terminal get for us the relevant section from

```
lsusb -v
```

---

### Post by flash63 on 2013-08-14
Hi,
[http://wikidevi.com/wiki/Belkin_F9L1106_v1](http://wikidevi.com/wiki/Belkin_F9L1106_v1)

ID:050D:1106 - Broadcom-Chipset (bad) &#8594; only with Ndiswrapper - but probably no Dualband-Support and some other problems ...

---

### Post by Bill_Sutton on 2013-08-14
Well I have tried lots and have come to he conclusion that a messy cable on the ground is better then a messed up head. 




Bus 002 Device 002: ID 050d:1106 Belkin Components 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x1106 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1

---

### Post by carl4926 on 2013-08-14
Looks like you'll be better in investing in a device that actually works.

---

### Post by Bucky Ball on 2013-08-14
Just out of curiousity, could you provide the output of this, with the dongle in:

```
sudo lshw -C network
```

@carl4926: Are you saying 'bad' to Broadcom wireless generally or just this model?

---

### Post by carl4926 on 2013-08-15
> **Bucky Ball said:**
> Just out of curiousity, could you provide the output of this, with the dongle in:

```
sudo lshw -C network
```

@carl4926: Are you saying 'bad' to Broadcom wireless generally or just this model?

Just this model it seems
I have broadcom myself that uses b43

There are plenty of USB devices that work OOTB and cheap too

---

### Post by Bucky Ball on 2013-08-15
> **carl4926 said:**
> There are plenty of USB devices that work OOTB and cheap too

Agreed. Don't throw this one away though! Probably will work in Ubuntu eventually, a bit down the track.

---

### Post by carl4926 on 2013-08-15
> **Bucky Ball said:**
> Agreed. Don't throw this one away though! Probably will work in Ubuntu eventually, a bit down the track.
The way I usually work is sell what doesn't work, reap some profit to assist the acquisition of what will work
Well at least it's my recommendation to the frequent individuals who can't find Ten bucks/quid for a wireless stick.

---

### Post by kurt18947 on 2013-08-15
> **carl4926 said:**
> The way I usually work is sell what doesn't work, reap some profit to assist the acquisition of what will work
Well at least it's my recommendation to the frequent individuals who can't find Ten bucks/quid for a wireless stick.

Yes, a little research before purchase is usually rewarded.  I've been known to write to the Chairman/President/CEO of firms that don't offer linux support.  Just to let them know I bought their competitor's product and why.  I have no illusion that one letter/email is going to matter but a couple dozen might.

---

### Post by Bucky Ball on 2013-08-15
> **kurt18947 said:**
> Yes, a little research before purchase is usually rewarded.  I've been known to write to the Chairman/President/CEO of firms that don't offer linux support.  Just to let them know I bought their competitor's product and why.  I have no illusion that one letter/email is going to matter but a couple dozen might.

Agreed and a recommended course of action.

---

### Post by Bill_Sutton on 2013-08-16
> **kurt18947 said:**
> Yes, a little research before purchase is usually rewarded.  I've been known to write to the Chairman/President/CEO of firms that don't offer linux support.  Just to let them know I bought their competitor's product and why.  I have no illusion that one letter/email is going to matter but a couple dozen might.

actually it worked brilliantly on my other PC but after swapping them around ( ie. moved to different rooms ) I then found it didnt like Ubuntu

have to say that when it comes to wireless that Windows wipes Ubuntu to the floor

---

### Post by Bucky Ball on 2013-08-16
> **Bill_Sutton said:**
> ... have to say that when it comes to wireless that Windows wipes Ubuntu to the floor

Has nothing to do with Ubuntu or Linux. As mentioned, notify the manufacturers about this. Also, a complete generalisation. Windows wipes the floor with your device. There are hundreds of others that work absolutely faultlessly (you don't have one) and some manufacturers that play nice with Linux. 

You can take the easy road and make sweeping statements based on your card and not much else, or, as a Linux user, you can do some research and purchase hardware you know will work in Linux. That simple.

As your card is a Broadcom and they are very well supported, no doubt your card will also work faultlessly in six months. Very new hardware often doesn't work, wireless or otherwise, because it takes unpaid devs a good deal of time to work it all out. If you actually wanted to help them get this card working you could see if there is a team working on this chipset and give them some input rather than make, probably out of frustration, wildly sweeping and ungrounded statements. Cheers.

---


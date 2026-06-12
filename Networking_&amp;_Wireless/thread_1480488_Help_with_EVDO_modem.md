---
title: "Help with EVDO modem"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Plankman on 2010-05-11
Hi there

I hope someone can help me. I'm running Ubuntu 10.04 in South Africa and I am using a Neotel telephone device that connects with EVDO.

I have followed instructions to get it working by typing:

sudo modprobe usbserial vendor=0x1d09 product=0x4000.

I have also put it in  /etc/init.d/rc.local to get it to load up on startup.

This works and I am able to connect using the network manager. The problem is if I disconnect and then try to connect again later, it refuses to connect till I reboot and then it works, till I disconnect again.

I'm not sure if I've done something wrong or missed something, so I'm hoping someone can help me out with a fix?

Thanks

---

### Post by alexfish on 2010-05-11
hi

normally if the sudo modprobe usbserial works then the details are entered in the ect/ modules

you could try

Code:



gksudo gedit /etc/modules


and  add the string

usbserial vendor=0x1d09 product=0x4000


see how it goes

---

### Post by Plankman on 2010-05-11
> **alexfish said:**
> 

gksudo gedit /etc/modules


and  add the string

usbserial vendor=0x1d09 product=0x4000


see how it goes

I tried it and still no good. Still does the same thing

---

### Post by alexfish on 2010-05-12
Hi

have you tried this modem with earlier versions of ubuntu

also can you do detailed output of the device 

Code:

lsusb -v

this output will be quite long so remove any usb devices not required

from the list can you identify the following lines similar to this ; my device may be different to yours , and post the results , also was the device configured in windows or other os before Ubuntu

Bus 001 Device 003: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x19d2 ONDA Communication S.p.A.
  idProduct          0x0031 ZTE MF636
  bcdDevice            0.00
  iManufacturer           2 ZTE,Incorporated
  iProduct                1 ZTE CDMA Technologies MSM
  iSerial                 3 1234567890ABCDEF
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
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
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32


regards

alexfish

---

### Post by Plankman on 2010-05-12
Hi axelfish

The phone/modem is a new edition I got a few months ago. It's been working fine in Vista, and it's the first time I'm using it with Ubuntu. Like I said, it does work in ubuntu, just when I've disconnected I can't reconnect till I've rebooted. I'll run that command tonight when I get home and post the output.

Thanks

---

### Post by Plankman on 2010-05-12
Ok

Here's my output, hope you can make sense of it and see something:

Bus 002 Device 003: ID 1d09:4000 TechFaith Wireless Technology Limited 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1d09 TechFaith Wireless Technology Limited
  idProduct          0x4000 
  bcdDevice            0.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

Thanks

---

### Post by alexfish on 2010-05-12
had a feeling it was a TechFaith device sure did a post similar to this device

not sure if it can be listed in the 10-modem.fdi under the evdo section 
or try to make a new entry /

will look at the listing in further detail

perhaps look at the fdi see what you think

it may work

also maybe remove the entry in the modules if it don't work

the only problem is the modem will connect but then after disconnecting seem to reset the device ,perhaps the modem is  as they say is falling asleep

be in touch soon . 

regards

 alexfish

---

### Post by Plankman on 2010-05-12
> **alexfish said:**
> 

the only problem is the modem will connect but then after disconnecting seem to reset the device ,perhaps the modem is  as they say is falling asleep



hey axelfish

I used your thinking that maybe it is falling asleep, so I tried switching it off and on again, and it connects. Don't know if that can help find a permanent solution, but at least it's easier than rebooting everytime I want to connect

---

### Post by alexfish on 2010-05-13
hi

been doing a bit of reading : techfaith specs ; according to data the on off can be done through the firmware of the device, so can assume when using the with windows and everything is working OK ,so then there must be an init code been sent ; IE AT + something 

there have been instances where  the init code ATZ should not be sent as this represents a reset state ; so the only init code it requires is the AT command

IE ; init1 = AT

If your using NM for the connection I could suggest using wvdial and see what happens

since I don't really know the modem it may be trial and error 

may be worth trying on Ubuntu 9.04 see what happens there and compare

just had another thought : sometimes when disconnecting through NM the modem manager still occupies the existing ports ; try killing the modem manager

---

### Post by Plankman on 2010-05-13
cool, will play with it tonight. At least I don't have to reboot each time now :)

---

### Post by Plankman on 2010-05-14
Seems like wvdial is a no go, unless I'm doing something wrong. I ran the config, it detected the modem and I edited the file with my username/password and phone number. When I try to connect, it start, but then it seems to hang and get nowhere.

---

### Post by alexfish on 2010-05-14
> **Plankman said:**
> Seems like wvdial is a no go, unless I'm doing something wrong. I ran the config, it detected the modem and I edited the file with my username/password and phone number. When I try to connect, it start, but then it seems to hang and get nowhere.


you will have to select the correct port : esp if the the modem has more than one control line:

from the terminal enter this code:

Code:

dmesg | grep -e "modem" -e "tty" 

then from this you can force the wvdial to select the correct port :

Try the different tty ports in wvdial.conf first

also the init strings differ for cdma and 3g

here is an example of a fairly new Modem 

[Dialer wana]
Modem Type = LG EVDO Rev.A USB Modem
Modem =  /dev/ttyUSB1 <===========pick from the list and  try them
Baud = 9600
ISDN = 0
Init1 = AT <========== this modem did not require the normal Init ATZ 
Init2 =  ATE0V1&D2&C1S0=0
Init3 = ATS7=60  <===========this was require my this modem but may not apply to yours
Init4 = ATS0=0 <===========this was require my this modem but may not apply to yours
Phone =  #777
Carrier Check = no <========this could be optional
New PPPD = yes
Username = wana
Password  = wana

the user of this modem resorted to a web search to find the correct dialling configs

regards

alexfish

---

### Post by Plankman on 2010-05-14
cool, will check it out tonight

---

### Post by Amerika1968 on 2011-07-29
Hi,
I am a problem with my CDMA EVDO express card AnyData APE-540H. With it I am connected to internet by Telefonica O2 provider.
With Win7 is all ok. But I installed Ubuntu 11.04 Natty. This OS sometimes recognize card as modem and connection is established, but only temporarily, for 1 - 2 hours. Mostly is recognize as CD ROM and connection is not working.
Can anybody help me? I am a beginner with ubuntu.
Thank you so much. Joseph.

---


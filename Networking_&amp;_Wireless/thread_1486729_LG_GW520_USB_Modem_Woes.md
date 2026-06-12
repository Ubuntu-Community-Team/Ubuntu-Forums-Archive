---
title: "LG GW520 USB Modem Woes"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by mchaggis on 2010-05-18
Hi folks,

I have been lumbered with a LG GW520 mobile phone as my upgrade and I am kinda regretting the decision, because I have now spend a couple of month trying to get this phone to be recognised as a modem. This phone (via windows) install a modem driver and then allows you to connect to the internet, so I know it's possible and this is how I am currently getting round the issue. However, I have hit a snag that is requires me to finally get ubuntu going with this phone and was hoping for a bit of help.

When connected, the phone prompts for what mode it should connect to the computer as (Mass storage, PC Suite, Music sync or Close). Under windows, you have to select PC Suite, so this is what I do (although I have tried the others, and Close does nothing). When PC Suite is selected, I execute 
```
dmesg
```
```

[ 4243.932202] usb 5-1: new full speed USB device using uhci_hcd and address 8
[ 4244.102521] usb 5-1: configuration #1 chosen from 1 choice
[ 4244.132502] scsi8 : SCSI emulation for USB Mass Storage devices
[ 4244.132785] usb-storage: device found at 8
[ 4244.132789] usb-storage: waiting for device to settle before scanning
[ 4249.129376] usb-storage: device scan complete
[ 4249.132490] scsi 8:0:0:0: CD-ROM            LGE      mobile           1.0  PQ: 0 ANSI: 0
[ 4249.160345] sr1: scsi-1 drive
[ 4249.160601] sr 8:0:0:0: Attached scsi CD-ROM sr1
[ 4249.160762] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 4249.720243] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 4249.724243] ISOFS: changing to secondary root

```

Now obviously this has now recognised the phone as a CD-ROM drive, which contains the windows software etc and isn't of much use.

The results of *lsusb*
```

Bus 005 Device 009: ID 1004:607f LG Electronics, Inc.

```

The results of *lsusb -d1004:607f*
```

Bus 005 Device 010: ID 1004:607f LG Electronics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1004 LG Electronics, Inc.
  idProduct          0x607f 
  bcdDevice            1.00
  iManufacturer           1 LG
  iProduct                2 LGE USB Device
  iSerial                 3 353638033836768
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 LGE USB Device
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 ms ifac 1 (::BULK_ONLY)
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

After some trawling I eventually stumbled upon *usb_modeswitch* which I thought might be the answer I was looking for, however, still no joy. 

Using SnoopyPro I can see the following:
```

USB\Vid_1004&Pid_6000&Rev_0100,USB\Vid_1004&Pid_6000    - LGE Mobile Composite USB Device
USB\VID_1004&PID_6000_DIAGInterface                     - LGE Mobile USB Serial Port (COM4)
USB\VID_1004&PID_6000_MODEMInterface                    - LGE Mobile Modem
USB\Vid_1004&Pid_6000&Rev_0100,USB\Vid_1004&Pid_607f    - USB Mass Storage Device

```

This seems to tally the 1004:607f seen via lsusb, however, it seems to indicate that for the modem, it should be 1004:6000?

So, I can edit */etc/usb-modeswitch.conf*
```

DefaultVendor= 0x1004
DefaultProduct=0x607f

TargetVendor=  0x1004
TargetProduct= 0x6000

```

However this doesn't work and I wonder if it is to do with the absence of MessageEndpoint and MessageContent options. However, I have no idea what I should have as values.

I realise that I may be barking up the wrong tree with all this, but I'm hoping that someone will be able to give me any pointers or tell me what I'm doing wrong.

---

### Post by alexfish on 2010-05-18
hi

which version of usb modeswitch are you using

and version of ubuntu

---

### Post by mchaggis on 2010-05-18
Ubuntu 10.04 - All updates
usb_modeswitch - Version 1.1.0 (C) Josua Dietze 2010

I have also tried inwi-usbmodem ([http://sourceforge.net/projects/lg-evdo-reva-us/](http://sourceforge.net/projects/lg-evdo-reva-us/)) top no avail :(

---

### Post by alexfish on 2010-05-18
hi

don't think any of them will help if the device is not listed

the only thing I can suggest is this

see if you can get the device to flip manually

plug the device in , if it mounts on the desk top the right click and "eject" or "safely remove"  then check to see if the device id's have changed

also check if it has been recognised with this command

Code:

dmesg | grep -e "modem" -e "tty"

this will indicate if the device is recognised as a modem and the ports 

if the device ID's have changed but not recognised as a modem then try

sudo modprobe usbserial vendor=0x1004 product=0x6000

check again with 

Code:

dmesg | grep -e "modem" -e "tty"

if successful 



Open /etc/modules by

Code:

gksudo gedit /etc/modules

and add the string

usbserial vendor=0x1004 product=0x6000

save and exit

Note if the device ID's are different to those done by snoopy then , substitute accordingly

---

### Post by mchaggis on 2010-05-18
When I Safely Remove or eject, the output from lsusb remains the same. So it looks like the phone is not supported at all under linux. Ho hum, that is a shame :(

---

### Post by alexfish on 2010-05-18
you try the usb modeswitch forum , 

mention you have snoopy installed , they may be able help guide you through the process

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

regards

alexfish

---

### Post by pdc on 2010-05-18
I see this device listed in the config file for the current usb_modeswitch which is 1.1.2 

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup)

> # LG HDM-2100 (EVDO Rev.A USB modem)
#
# Contributor: Jérôme Oufella

;DefaultVendor= 0x1004
;**DefaultProduct**=0x**607f**

;TargetVendor=  0x1004
;**TargetProduct**= 0x**6114**

# only for reference and 0.x versions
# MessageEndpoint=8

;MessageContent="1201100102000040041014610000010200018006000100001200"



you can get the latest version from here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

as these are debian repositories;

Josh says the advantage of the latest version is it should auto-configure

---

### Post by mchaggis on 2010-05-19
Unfortunately I have just sent my phone off to have the phone's software "reinstalled" as it developed an annoying habit of deleting contacts randomly. When I get it back I shall let you know if I have any further success :-S

Thanks for you help

---

### Post by alexfish on 2010-05-19
hi

there has been a recent post at the modeswitch forum with similar ID's

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=402](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=402)

---


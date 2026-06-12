---
title: "TV Tuner - USB - Gigabyte U8000 Hybrid Tv Dogle (Analog+Digital)"
date: 2008-05-19
forum: Multimedia Software
---

### Post by vboblinux on 2008-05-19
Hi all, I have a usb TV Tuner the "Gigabyte U8000". It is a Hybrid Tv Dogle (Tv Analog+Tv Digital + Radio).

Is it possible to make it work in my Ubuntu 8.04?
What should I do to install it? What program should I use to play and record tv programs?

Here are the results of my terminal using the "lsusb" command that might be useful.

> ~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 1044:7002 Chu Yuen Enterprise Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 056a:0015 Wacom Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
 


Thank you a priori for your help. :)

Edit: Here is a link I found with maybe some more technical information that might help more.
[http://www.tweaktown.com/reviews/1156/gigabyte_gt_u8000_rh_digital_tv_tuner/](http://www.tweaktown.com/reviews/1156/gigabyte_gt_u8000_rh_digital_tv_tuner/)

---

### Post by aresthedog on 2008-09-12
Works great for me:

[http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html](http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html)

---

### Post by lovinglinux on 2008-09-12
To watch TV I would recommend TVTime. Is the most popular and efficient program. You can download from the repositories using the Add/Remove Manager.

If you want a full feature Media Center, that you can use to record and stream all over your network, you can install MythTV. It is also in the repositories. This is much more complex to configure.

If you want some benefits of a Media Center, but control everything from inside your browser, you can try my [[COLOR="Red"]**Firefox Media Center tutorial**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5748047"). Even if you don't like the idea of using Firefox, the tutorial explains how to record and stream video.

---

### Post by vboblinux on 2008-09-12
Thank you very much for your answer. I will try it...!!! :)

---

### Post by Cresho on 2008-09-12
I use TVtime to record videos through transcode.  It is much better than the bloated mythtv.  If you need to know, ill post on this thread.  Here is a pic so you can see how easy it looks with record buttons and all.

---

### Post by vboblinux on 2008-09-13
Yes, it seems pretty easy to record a video in the screenshot.
I already downloaded the two files (firmware) but right now my tuner is in the hands of a friend of mine (he went a trip in another country and he needed it to watch the Olympic Games on the laptop and I gave it to him until he gets back hehe).Now he is back. I will take it back soon (maybe today). Then I will try to install it to my 8.04 Linux.
If I find any difficulties at installation time I will post here for help.

:)

---

### Post by vboblinux on 2008-09-15
Today I got back my tv-tuner from my friend. :-)

OK. I need a little help here.
Here is what I did until now:

1. I Downloaded the two firmware files and renamed if needed. (dvb-usb-dib0700-1.10.fw and xc3028-v27.fw)

2. I Copied them into the folder /lib/firmware

```
cp dvb-usb-dib0700-1.10.fw /lib/firmware
```
```
cp xc3028-v27.fw /lib/firmware
```


3. I Tried to locate the file "dvb-usb-ids.h" using the command
```
sudo find / -name dvb-usb-ids.h
```

At step 3 I found that it is at /home/user/.gvfs
I Used the command 
```
sudo gedit dvb-usb-ids.h
```
Permission denied
I went to the directory "/home/user/.gvfs" and found nothing inside.
I tried to create the dvb-usb-ids.h file manually (as a text file) and then put inside the text that was written in the page you showed me. 
What exactly should I put inside the file? Should I create that file or should I find it inside another directory?

(I wanted to ask before I Proceed to be sure that I am doing it right).

Thanks a priori for your answer. :-)

---

### Post by Cresho on 2008-09-17
we first need to see if your usb tuner is working.

can you verify if it is?

lsusb -vnn

also try 

ls -l /dev/dvb/adapter0

and or this one.  just because i dont know if yours is digital or what

ls -l /dev/video0

ls -l /dev/video1

---

### Post by vboblinux on 2008-09-18
My tuner is the Analog and digital one (Hybrid).It have radio too. (Check my first post)
It is working (not broken)
It is not Working in my Linux.
I can verify that (for example) the little green light on my tuner is not turned on. (I believe that is an indication that it is not recognized in my linux system). 

The command 
```
lsusb -vnn
```

gives the following result (the -n parameter does not exist as far as I understand from the result).


```
lsusb: invalid option -- n
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program

```


I tried the lsusb -v command but it seems the result is too big and cant scroll up in the console to copy/paste it all (I don't know how to scroll up).

Here are the results of the console of the rest.
```

ls -l /dev/dvb/adapter0
```
```
ls: cannot access /dev/dvb/adapter0: No such file or directory
```


```
ls -l /dev/video0
```
```
ls: cannot access /dev/video0: No such file or directory
```


```
ls -l /dev/video1 
```
```
ls: cannot access /dev/video1: No such file or directory
```



and here are the results in the console for the 
```
sudo lsusb -v
```


```
 Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x01a8  1x 424 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0212  1x 530 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x027c  1x 636 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x031b  1x 795 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0385  1x 901 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       8
      bNumEndpoints           1
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ef  1x 1007 bytes
        bInterval               1
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

Bus 005 Device 002: ID 056a:0015 Wacom Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x056a Wacom Co., Ltd
  idProduct          0x0015 
  bcdDevice            4.03
  iManufacturer           1 WACOM
  iProduct                6 CTE-440-U V4.0-3
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               40mA
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
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      98
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 005 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-17-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-17-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-17-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-17-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.1
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-17-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.0
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
vagelis@vaglinux:~$ us, Operation not permitted (1)
bash: syntax error near unexpected token `('
```



any ideas? :confused:

---

### Post by Cresho on 2008-09-18
ya that was a typo.  I hope I can help you here!
just a little info about past tuner cards (no usb expirience tuner mind you but I would like to learn)
I have 2 tutorials in setting up a high definition card on 2 pc's with 2 tuners and also have a tvtime with video record enabled for video input and television channels using transcode.  So I do have expirience.

this link shows about them getting it to work or something in that area

[http://www.uluga.ubuntuforums.org/showthread.php?t=853987](http://www.uluga.ubuntuforums.org/showthread.php?t=853987)

dmesg output here as well.  As far as I can tell, your usb is not running.  after we get the correct firmware running with the usb, then we can talk about software.

Let me know whats going on.

---

### Post by Cresho on 2008-09-18
ya that was a typo.  I hope I can help you here!
just a little info about past tuner cards (no usb card expirience mind you but I would like to learn)
I have 2 tutorials in setting up a high definition card on 2 pc's with 2 tuners and also have a tvtime with video record enabled for video input and television channels using transcode.  So I do have expirience.

this link shows about them getting it to work or something in that area

[http://www.uluga.ubuntuforums.org/showthread.php?t=853987](http://www.uluga.ubuntuforums.org/showthread.php?t=853987)

dmesg output here as well.  As far as I can tell, your usb is not running.  after we get the correct firmware running with the usb, then we can talk about software.

Let me know whats going on.

---

### Post by Cresho on 2008-09-18
ohh crap I forgot to tell you that some of the usb devices require power from the usb itself.  Try plugging it in on your usb that is on your motherboard and not from the pc case.  I know it's a longshot and you mentioned that you have it working under windows but you did not say if you are using the same usb slot.

check if the light on the usb is on.

also check if the light is on during boot or does it initiate itself on a windows base  machine only with or without drivers?

then look at this post

[http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html](http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html)

make sure its the same usb tv tuner!

---

### Post by vboblinux on 2008-09-18
It seems that I am confused. :-(
The only steps I have completed from the help URL:
[http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html](http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html)
was the downloading of the two firmware files and the copy/paste to the "/lib/firmware" path in my system...!!!

Where exactly should I look to find the "dvb-usb-ids.h" file???
In what folder is that file?

Here are the results of the "dmesg" command in my system:

```
[   26.733158] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   26.733260] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   26.733360] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   26.733460] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[   26.733559] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   26.733661] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   26.733765] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[   26.733866] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   26.734014] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.734059] pnp: PnP ACPI init
[   26.734067] ACPI: bus type pnp registered
[   26.736748] pnpacpi: exceeded the max number of mem resources: 12
[   26.736918] pnp: PnP ACPI: found 15 devices
[   26.736921] ACPI: ACPI bus type pnp unregistered
[   26.736926] PnPBIOS: Disabled by ACPI PNP
[   26.737226] PCI: Using ACPI for IRQ routing
[   26.737230] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.792622] NET: Registered protocol family 8
[   26.792624] NET: Registered protocol family 20
[   26.792699] AppArmor: AppArmor Filesystem Enabled
[   26.796482] Time: tsc clocksource has been installed.
[   26.808696] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   26.808699] system 00:01: ioport range 0x290-0x29f has been reserved
[   26.808702] system 00:01: ioport range 0x800-0x87f has been reserved
[   26.808704] system 00:01: ioport range 0x290-0x294 has been reserved
[   26.808707] system 00:01: ioport range 0x880-0x88f has been reserved
[   26.808720] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[   26.808727] system 00:0c: iomem range 0xd8000000-0xdbffffff could not be reserved
[   26.808733] system 00:0d: iomem range 0xcee00-0xcffff has been reserved
[   26.808736] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   26.808739] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   26.808742] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   26.808745] system 00:0d: iomem range 0x7fff0000-0x7fffffff could not be reserved
[   26.808747] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   26.808750] system 00:0d: iomem range 0x100000-0x7ffeffff could not be reserved
[   26.808753] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[   26.808756] system 00:0d: iomem range 0xfed13000-0xfed1dfff could not be reserved
[   26.808759] system 00:0d: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   26.808762] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   26.808765] system 00:0d: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   26.839265] PCI: Bridge: 0000:00:01.0
[   26.839267]   IO window: disabled.
[   26.839272]   MEM window: d0000000-d7ffffff
[   26.839276]   PREFETCH window: c0000000-cfffffff
[   26.839280] PCI: Bridge: 0000:00:1c.0
[   26.839283]   IO window: 6000-6fff
[   26.839288]   MEM window: disabled.
[   26.839291]   PREFETCH window: disabled.
[   26.839296] PCI: Bridge: 0000:00:1c.3
[   26.839299]   IO window: 7000-8fff
[   26.839304]   MEM window: df100000-df1fffff
[   26.839308]   PREFETCH window: disabled.
[   26.839313] PCI: Bridge: 0000:00:1c.4
[   26.839316]   IO window: 9000-9fff
[   26.839321]   MEM window: dc000000-ddffffff
[   26.839325]   PREFETCH window: 88000000-880fffff
[   26.839330] PCI: Bridge: 0000:00:1e.0
[   26.839331]   IO window: disabled.
[   26.839336]   MEM window: df000000-df0fffff
[   26.839340]   PREFETCH window: de000000-deffffff
[   26.839355] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.839361] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.839381] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.839387] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.839406] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[   26.839411] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   26.839429] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   26.839434] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   26.839445] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   26.839456] NET: Registered protocol family 2
[   26.876756] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.877057] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.877633] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.877917] TCP: Hash tables configured (established 131072 bind 65536)
[   26.877920] TCP reno registered
[   26.888868] checking if image is initramfs... it is
[   27.339757] Switched to high resolution mode on CPU 0
[   27.339882] Switched to high resolution mode on CPU 1
[   27.484317] Freeing initrd memory: 7672k freed
[   27.485180] audit: initializing netlink socket (disabled)
[   27.485191] audit(1221768983.332:1): initialized
[   27.485413] highmem bounce pool size: 64 pages
[   27.487808] VFS: Disk quotas dquot_6.5.1
[   27.487902] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.488047] io scheduler noop registered
[   27.488050] io scheduler anticipatory registered
[   27.488052] io scheduler deadline registered
[   27.488063] io scheduler cfq registered (default)
[   27.488185] Boot video device is 0000:01:00.0
[   27.488316] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.488357] assign_interrupt_mode Found MSI capability
[   27.488389] Allocate Port Service[0000:00:01.0:pcie00]
[   27.488483] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.488525] assign_interrupt_mode Found MSI capability
[   27.488560] Allocate Port Service[0000:00:1c.0:pcie00]
[   27.488606] Allocate Port Service[0000:00:1c.0:pcie02]
[   27.488701] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.488744] assign_interrupt_mode Found MSI capability
[   27.488779] Allocate Port Service[0000:00:1c.3:pcie00]
[   27.488824] Allocate Port Service[0000:00:1c.3:pcie02]
[   27.488919] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   27.488961] assign_interrupt_mode Found MSI capability
[   27.488996] Allocate Port Service[0000:00:1c.4:pcie00]
[   27.489038] Allocate Port Service[0000:00:1c.4:pcie02]
[   27.489351] isapnp: Scanning for PnP cards...
[   27.840369] isapnp: No Plug & Play device found
[   27.877211] Real Time Clock Driver v1.12ac
[   27.877327] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.877452] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.878202] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.878434] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 18
[   27.878442] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   27.879272] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.879348] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.879486] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   27.879819] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.879826] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.906612] mice: PS/2 mouse device common for all mice
[   27.906770] EISA: Probing bus 0 at eisa.0
[   27.906791] Cannot allocate resource for EISA slot 6
[   27.906793] Cannot allocate resource for EISA slot 7
[   27.906795] Cannot allocate resource for EISA slot 8
[   27.906797] EISA: Detected 0 cards.
[   27.906800] cpuidle: using governor ladder
[   27.906802] cpuidle: using governor menu
[   27.906876] NET: Registered protocol family 1
[   27.906905] Using IPI No-Shortcut mode
[   27.906932] registered taskstats version 1
[   27.907045]   Magic number: 8:213:296
[   27.907062]   hash matches device ttywd
[   27.907111]   hash matches device tty29
[   27.907133] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.907135] EDD information not available.
[   27.907303] Freeing unused kernel memory: 368k freed
[   27.924388] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   29.145015] fuse init (API version 7.9)
[   29.167788] ACPI: Processor [CPU0] (supports 2 throttling states)
[   29.167823] ACPI: Processor [CPU1] (supports 2 throttling states)
[   29.167842] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.167856] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.360380] usbcore: registered new interface driver usbfs
[   29.360413] usbcore: registered new interface driver hub
[   29.361109] usbcore: registered new device driver usb
[   29.363502] USB Universal Host Controller Interface driver v3.0
[   29.363560] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.363574] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   29.363579] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   29.363811] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   29.363850] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a000
[   29.364045] usb usb1: configuration #1 chosen from 1 choice
[   29.364088] hub 1-0:1.0: USB hub found
[   29.364098] hub 1-0:1.0: 2 ports detected
[   29.467627] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   29.467643] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   29.467649] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   29.467684] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   29.467717] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000a400
[   29.467889] usb usb2: configuration #1 chosen from 1 choice
[   29.467939] hub 2-0:1.0: USB hub found
[   29.467950] hub 2-0:1.0: 2 ports detected
[   29.571447] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   29.571464] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.571470] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.571505] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   29.571536] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000a800
[   29.571696] usb usb3: configuration #1 chosen from 1 choice
[   29.571733] hub 3-0:1.0: USB hub found
[   29.571741] hub 3-0:1.0: 2 ports detected
[   29.675225] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   29.675242] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.675248] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.675286] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   29.675321] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ac00
[   29.675501] usb usb4: configuration #1 chosen from 1 choice
[   29.675541] hub 4-0:1.0: USB hub found
[   29.675550] hub 4-0:1.0: 2 ports detected
[   29.707071] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   29.779038] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   29.779053] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.779059] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.779094] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   29.779126] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000b000
[   29.779299] usb usb5: configuration #1 chosen from 1 choice
[   29.779340] hub 5-0:1.0: USB hub found
[   29.779349] hub 5-0:1.0: 2 ports detected
[   29.866250] SCSI subsystem initialized
[   29.871094] usb 1-1: configuration #1 chosen from 1 choice
[   29.882913] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
[   29.882931] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   29.882937] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   29.882973] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   29.886875] PCI: cache line size of 128 is not supported by device 0000:00:1a.7
[   29.886885] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xdf204000
[   29.903760] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.903927] usb usb6: configuration #1 chosen from 1 choice
[   29.903970] hub 6-0:1.0: USB hub found
[   29.903980] hub 6-0:1.0: 4 ports detected
[   29.939470] Floppy drive(s): fd0 is 1.44M
[   29.959517] libata version 3.00 loaded.
[   29.960244] FDC 0 is a post-1991 82077
[   30.007787] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   30.007806] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   30.007812] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   30.007849] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   30.011766] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   30.011777] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf205000
[   30.027455] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.027630] usb usb7: configuration #1 chosen from 1 choice
[   30.027672] hub 7-0:1.0: USB hub found
[   30.027682] hub 7-0:1.0: 6 ports detected
[   30.131415] ahci 0000:03:00.0: version 3.0
[   30.131447] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   30.526523] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   30.658288] usb 6-1: configuration #1 chosen from 1 choice
[   30.896841] usb 6-3: new high speed USB device using ehci_hcd and address 3
[   31.030075] usb 6-3: configuration #1 chosen from 1 choice
[   31.030361] hub 6-3:1.0: USB hub found
[   31.030703] hub 6-3:1.0: 4 ports detected
[   31.132415] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   31.132420] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   31.132426] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   31.132665] usb 1-1: USB disconnect, address 2
[   31.133004] scsi0 : ahci
[   31.133081] scsi1 : ahci
[   31.133135] ata1: SATA max UDMA/133 abar m8192@0xdf100000 port 0xdf100100 irq 17
[   31.133142] ata2: SATA max UDMA/133 abar m8192@0xdf100000 port 0xdf100180 irq 17
[   31.451806] ata1: SATA link down (SStatus 0 SControl 300)
[   31.771220] ata2: SATA link down (SStatus 0 SControl 300)
[   31.777279] ata_piix 0000:00:1f.2: version 2.12
[   31.777289] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   31.926923] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   31.930920] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
[   31.930955] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   31.931003] scsi2 : ata_piix
[   31.931231] scsi3 : ata_piix
[   31.931896] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xc400 irq 17
[   31.931899] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xc408 irq 17
[   32.101023] usb 5-1: configuration #1 chosen from 1 choice
[   32.106774] ata3.00: HPA unlocked: 390715759 -> 390721968, native 390721968
[   32.106781] ata3.00: ATA-6: WDC WD2000JD-00HBB0, 08.02D08, max UDMA/133
[   32.106784] ata3.00: 390721968 sectors, multi 16: LBA48 
[   32.124075] ata3.00: configured for UDMA/133
[   32.305421] ata4.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[   32.305426] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
[   32.318540] ata4.00: configured for UDMA/133
[   32.318666] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JD-00H 08.0 PQ: 0 ANSI: 5
[   32.318838] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[   32.318931] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   32.318966] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
[   32.319007] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   32.319057] scsi4 : ata_piix
[   32.319125] scsi5 : ata_piix
[   32.319630] ata5: SATA max UDMA/133 cmd 0xd000 ctl 0xd400 bmdma 0xe000 irq 17
[   32.319636] ata6: SATA max UDMA/133 cmd 0xd800 ctl 0xdc00 bmdma 0xe008 irq 17
[   32.342150] usb 5-2: new full speed USB device using uhci_hcd and address 3
[   32.499274] ata5.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   32.499278] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (not used)
[   32.503284] usb 5-2: configuration #1 chosen from 1 choice
[   32.515296] ata5.00: configured for UDMA/133
[   32.556406] usbcore: registered new interface driver hiddev
[   32.556458] usbcore: registered new interface driver usbhid
[   32.556465] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.679799] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   32.682681] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   32.682690] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
[   32.682733] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   32.682788] scsi6 : pata_jmicron
[   32.683021] scsi7 : pata_jmicron
[   32.683065] ata7: PATA max UDMA/100 cmd 0x7000 ctl 0x7400 bmdma 0x8000 irq 16
[   32.683069] ata8: PATA max UDMA/100 cmd 0x7800 ctl 0x7c00 bmdma 0x8008 irq 16
[   33.010402] ata7.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A102, max UDMA/33
[   33.017383] ata7.01: HPA unlocked: 117229295 -> 117231408, native 117231408
[   33.017389] ata7.01: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
[   33.017391] ata7.01: 117231408 sectors, multi 16: LBA 
[   33.189072] ata7.00: configured for UDMA/33
[   33.205937] ata7.01: configured for UDMA/100
[   33.374413] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A102 PQ: 0 ANSI: 5
[   33.374589] scsi 6:0:1:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
[   33.389812] Driver 'sd' needs updating - please use bus_type methods
[   33.389922] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   33.389944] sd 2:0:0:0: [sda] Write Protect is off
[   33.389949] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.389982] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.390054] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   33.390072] sd 2:0:0:0: [sda] Write Protect is off
[   33.390077] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.390110] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.390116]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   33.405000]  sda1 sda2 < sda5 >
[   33.415344] sd 2:0:0:0: [sda] Attached SCSI disk
[   33.415431] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   33.415453] sd 3:0:0:0: [sdb] Write Protect is off
[   33.415458] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   33.415491] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.415562] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   33.415581] sd 3:0:0:0: [sdb] Write Protect is off
[   33.415585] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   33.415616] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.415621]  sdb: sdb1 sdb2 < sdb5 >
[   33.426127] sd 3:0:0:0: [sdb] Attached SCSI disk
[   33.426202] sd 4:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   33.426222] sd 4:0:0:0: [sdc] Write Protect is off
[   33.426226] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   33.426259] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.426328] sd 4:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   33.426350] sd 4:0:0:0: [sdc] Write Protect is off
[   33.426354] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   33.426384] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.426390]  sdc: sdc1 sdc2
[   33.431636] sd 4:0:0:0: [sdc] Attached SCSI disk
[   33.450413] sd 6:0:1:0: [sdd] 117231408 512-byte hardware sectors (60022 MB)
[   33.450420] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.450428] Uniform CD-ROM driver Revision: 3.20
[   33.450450] sd 6:0:1:0: [sdd] Write Protect is off
[   33.450455] sd 6:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   33.450490] sd 6:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.450560] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   33.450624] sd 6:0:1:0: [sdd] 117231408 512-byte hardware sectors (60022 MB)
[   33.450643] sd 6:0:1:0: [sdd] Write Protect is off
[   33.450647] sd 6:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   33.450684] sd 6:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.450690]  sdd: sdd1 sdd2 sdd3
[   33.482193] sd 6:0:1:0: [sdd] Attached SCSI disk
[   33.490260] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   33.490292] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   33.490324] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   33.490356] sr 6:0:0:0: Attached scsi generic sg3 type 5
[   33.490390] sd 6:0:1:0: Attached scsi generic sg4 type 0
[   33.861072] Attempting manual resume
[   33.861076] swsusp: Resume From Partition 8:50
[   33.861078] PM: Checking swsusp image.
[   33.861251] PM: Resume from disk failed.
[   33.902101] kjournald starting.  Commit interval 5 seconds
[   33.902114] EXT3-fs: mounted filesystem with ordered data mode.
[   43.242910] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.285734] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   44.297861] Linux agpgart interface v0.102
[   44.356841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.389543] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.932898] input: Power Button (FF) as /devices/virtual/input/input2
[   44.958555] ACPI: Power Button (FF) [PWRF]
[   44.958676] input: Power Button (CM) as /devices/virtual/input/input3
[   44.970531] ACPI: Power Button (CM) [PWRB]
[   45.211277] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.211293] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   45.211325] sky2 0000:04:00.0: v1.20 addr 0xdd000000 irq 16 Yukon-EC (0xb6) rev 2
[   45.212600] sky2 eth0: addr 00:16:e6:59:05:c5
[   45.486008] nvidia: module license 'NVIDIA' taints kernel.
[   46.210664] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   46.210696] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   46.829179] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.829190] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   46.829332] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   47.577725] iTCO_vendor_support: vendor-support=0
[   47.590052] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   47.590163] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
[   47.590207] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   47.660494] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   48.603866] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 21
[   48.656144] phy0: Selected rate control algorithm 'simple'
[   48.726342] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   48.843496] input: Wacom Graphire4 4x5 as /devices/pci0000:00/0000:00:1d.2/usb5/5-1/5-1:1.0/input/input6
[   48.875255] usbcore: registered new interface driver wacom
[   48.875262] /build/buildd/linux-2.6.24/drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver
[   49.101495] [ueagle-atm] driver ueagle 1.4 loaded
[   49.101552] usb 5-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9031) Rev (0X200B): Eagle III
[   49.210623] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[   49.230162] parport_pc 00:08: reported by Plug and Play ACPI
[   49.230213] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   49.417239] usb 5-2: [ueagle-atm] using iso mode
[   49.422115] usb 5-2: [ueagle-atm] (re)booting started
[   49.424037] usbcore: registered new interface driver ueagle-atm
[   51.017127] lp0: using parport0 (interrupt-driven).
[   51.133850] usb 5-2: [ueagle-atm] ATU-R firmware version : 44e2ea17
[   51.135636] usb 5-2: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
[   51.147166] usb 5-2: [Ueagle-atm] use deprecated cmvs version, please update your firmware
[   51.187765] usb 5-2: [ueagle-atm] modem started, waiting synchronization...
[   51.203137] Adding 1951888k swap on /dev/sdd2.  Priority:-1 extents:1 across:1951888k
[   51.769044] EXT3 FS on sdd1, internal journal
[   51.929674] device-mapper: uevent: version 1.0.3
[   51.929716] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   53.870509] No dock devices found.
[   55.300875] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   55.300882] apm: disabled - APM is not SMP safe.
[   55.415996] ppdev: user-space parallel port driver
[   55.612193] audit(1221758214.737:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5666 profile="/usr/sbin/cupsd" namespace="default"
[   57.681129] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   57.681137] vboxdrv: Successfully done.
[   57.681140] vboxdrv: Found 2 processor cores.
[   57.681161] vboxdrv: fAsync=0 u64DiffCores=4417.
[   57.681221] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   57.681226] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   57.954887] tun: Universal TUN/TAP device driver, 1.6
[   57.954894] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   60.432606] sky2 eth0: enabling interface
[   60.449404] Bluetooth: Core ver 2.11
[   60.449827] NET: Registered protocol family 31
[   60.449832] Bluetooth: HCI device and connection manager initialized
[   60.449839] Bluetooth: HCI socket layer initialized
[   60.468227] Bluetooth: L2CAP ver 2.9
[   60.468233] Bluetooth: L2CAP socket layer initialized
[   60.567452] Bluetooth: RFCOMM socket layer initialized
[   60.567491] Bluetooth: RFCOMM TTY layer initialized
[   60.567494] Bluetooth: RFCOMM ver 1.8
[   62.177518] usb 5-2: [ueagle-atm] modem operational
[   64.869604] PPP generic driver version 2.4.2
[   65.028684] NET: Registered protocol family 10
[   65.029213] lo: Disabled Privacy Extensions
[   65.030225] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   65.030999] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```



I believe that to be able to set up my tuner to work in my Linux the only way to do it correct is to tel me what to do "step by step"...:-(
(But still the good news are the reports of all you people that say that the tuner is working great in Linux...!!! :-) It would be nice to be easier though...!!! )

Edit: From the first time I had my tuner pluged in the usb from my motherboard (because of the power consumption it needs). :-)
I will do a restart now to check the little LED light if it is turning on during boot. 
It is the Gigabyte U8000 Analog+Digital tv-tuner. I will take my digital camera and take some shots of my tuner and the box to show you...:-) :D

---

### Post by vboblinux on 2008-09-18
The exact model name is "GT-U8000-RH" (from the barcode on the box)
Gigabyte U8000 USB 2.0 Hybrid TV Dongle [Analog+Digital] are the letters on the box of the tuner.

Here are the photos I took.


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85654&stc=1&d=1221755483[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85656&stc=1&d=1221755683[/IMG]


Edit: During boot time, I checked the LED light of the tv-tuner and it **_didn't_** turned on at all and at any time...

---

### Post by Cresho on 2008-09-18
so when it is running under windows, the light is on? or does it get activated when you turn on the software?

in linux, is the light on at anytime?  I need to know what triggers it on first of all.

---

### Post by vboblinux on 2008-09-19
Windows: Light is off but when I run the software to watch tv then it turns on.

Linux: off all the time and When I run the TvTime it says that I have no input.

Today in the morning when I opened my computer it booted linux normally.
I did a restart and then after a while (at booting time) the monitor got black and the HDD didn't seem to read at all.
I waited a little and then I pressed the hardware reset button.
I was booting to linux again and the same thing happened (black screen). Then I hardware restarted my pc again but this time I had my tv-tuner unplugged and my computer loaded normally to my linux. 
Then I had to go to my work (didn't have time to make more tests).

It seems that maybe (?) we are in a good way with tunner. That blank (black) screen at boot time might be the wrong identification of the tuner...or something..!!! (?)

---

### Post by Cresho on 2008-09-19
okay, now I read this thread again.  I had to because I know i missed something.  That guy who has it should of helped but he must be sleeping..zzz

I hope he comes in and throws some comments.


you did mess up.  you cp and you did not go into super user mode.  That directory is not accessable normaly.

do this

gksudo nautilus /lib/firmware

and see if those files are in there, if not, just drag and drop them in there.  then reboot your computer and do a dmesg and see if it is in there.

your filebrowser is in super user mode so you can just drag them in there.

post your output.  or play with me-tv or something.  If you cant get it to work, we will try the v4l step with that crazy dvb-usb-ids.h file that is not on your system.  We might need to compile a v4l dvb from source and this part is easy.  I just don't know if we really need to compile one from source. since its already on your system.

if me-tv turns on your high definition tuner, turn it off right away.  I pretty much have me-tv figured and the tools it comes with is not good enough to detect any atsc signals but we have a tool that can create such a file needed for television viewing.

---

### Post by vboblinux on 2008-09-19
hmm....I thing I understand what is going on...!!! Maybe the "dvb-usb-ids.h" is part of the kernel before compiling. (I don't know how to compile a kernel yet). That's why I can't locate it in my system...!!! (can anyone give me the correct path of the file to check If i can find it?)

So I should follow the instructions listed [Here]("https://help.ubuntu.com/community/Kernel/Compile") and prepare the kernel for compile. Then inside the files of the "kernel for compile" I will find the "dvb-usb-ids.h" and then change it according to the instructions listed [Here]("http://linuxtv.org/pipermail/linux-dvb/2008-August/028108.html"). After that the kernel will be patched and the system should treat my tuner like it is the Terratec Cinergy HT USB XE tv tuner.
Then I should change the grub in a way that it should load the new (patched) kernel. (I am not sure that I know how to load the patched kernel in  grub..) 

Then I should reboot my computer and when I boot to my 8.04 linux with the new kernel, I should plugin my tv-tunner.

Using the "dmesg" command I could verify that the tunner is running in the patched kernel. 

Then I should open the tvtime or whatever program is used to watch tv in linux and it should work...!!!
Then when the new kernel is out, IF support team didn't add to the new kernel the U8000 Tv-Tuner I should patch the new kernel too - the same way - to make it work there too...!!!

So the hard part is to compile the (patched) kernel...

Am I correct? Or I am missing something?

Edit: Now I saw your comment Cresto. I can verify that the two firmware files are in the /lib/firmware because I used the sudo command (I remember that I went for a while with the "sudo su" command to avoid adding the password all the time and then I did a restart (Didn't know how to get back to a normal user after using the sudo su command - so I did a restart to be safe and to check if the firmware was loaded after the restart). I also saw them in the /lib/firmware (I am at work right now and I don't have linux here) folder after the copy. So that part of the tuner installation went ok. :-)

---

### Post by saperduper on 2008-10-20
I followed the instructions given in this excellent howto **[http://www.linuxtv.org/wiki/index.php/Gigabyte_U8000-RH](http://www.linuxtv.org/wiki/index.php/Gigabyte_U8000-RH)** and it worked like a charm.

The sad thing is that currently **only DVB-T digital TV/HDTV is working** because there is **[COLOR="Red"]no driver written[/COLOR] for the CX25843-24Z audio/video decoder** which is probably used for the **analogue TV/FM radio** portion of the device.

---

### Post by Cresho on 2008-10-21
i used this as well but it will not let my nvidia card work after install.  it works fine but as long as I have no nvidia graphics accelerator.

---

### Post by Heatseeker on 2009-10-11
Hi, is there anything new with watching analog TV with this tuner under linux?

---


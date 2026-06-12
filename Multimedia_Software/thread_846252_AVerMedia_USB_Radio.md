---
title: "AVerMedia USB Radio"
date: 2008-07-01
forum: Multimedia Software
---

### Post by kaefert66014235 on 2008-07-01
I have found some old analog radio USB-Stick and wanted to look if i can get it to work with Ubuntu 8.04

Here are some details:
```
kaefert@Mobulux:~$ sudo lsusb -s 004:002 -v
Bus 004 Device 002: ID 07ca:b800 AVerMedia Technologies, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x07ca AVerMedia Technologies, Inc.
  idProduct          0xb800 
  bcdDevice            0.03
  iManufacturer           1 AVerMedia Technologies
  iProduct                2 AVerMedia USB Radio
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 HID Device
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
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
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval             120
Device Status:     0x0000
  (Bus Powered)
kaefert@Mobulux:~$
```

```
cat /proc/bus/usb/devices
......
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=07ca ProdID=b800 Rev= 0.03
S:  Manufacturer=AVerMedia Technologies
S:  Product=AVerMedia USB Radio
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=200mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=255ms
E:  Ad=02(O) Atr=03(Int.) MxPS=   8 Ivl=120ms
......
```

Now it would be nice to if someone could tell me how to get some program to control the frequence and to play the audio of that FM-radio USB-Stick

---

### Post by vivedekananda on 2008-07-17
first you should try to get some drivers for the stick, try avermedia website:
[www.avermedia.com](www.avermedia.com)

they have linux drivers for some of their products, eg avertv hybrid+fm volar;
the drivers come with some utilities which allow you to set frequency in the source code, quite easy if you know C/C++,see eg ratio-player.c

---

### Post by taeuber on 2009-03-05
Hi there.

Here is a very nice programm that works for me for some years now:
[http://av-usbradio.sourceforge.net/index.php]("http://av-usbradio.sourceforge.net/index.php")

The download is possible here:
[http://sourceforge.net/project/showfiles.php?group_id=124933&package_id=137649]("http://sourceforge.net/project/showfiles.php?group_id=124933&package_id=137649")

regards
Lars

---

### Post by despotakisch on 2009-04-18
The program which taueber proposes works fine in ubuntu 8.10 but it doesn't work in ubuntu 9.04 beta for me. Have anybody else the same problem? How can I solve this?

---

### Post by Alexey Klimov on 2009-05-28
> **despotakisch said:**
> The program which taueber proposes works fine in ubuntu 8.10 but it doesn't work in ubuntu 9.04 beta for me. Have anybody else the same problem? How can I solve this?

Hello,

I don't remember what kernel version inside ubuntu 8.10, so..

I wrote driver for this radio, and it was merged in v4l branch since 2.6.28.
But driver works fine since 2.6.29 kernel..

If i'm not wrong ubuntu 9.04 use 2.6.28 kernel. So, it has first workin version of this driver 0.01. When you plug radio in, you can see in dmesg log, that driver is loaded :)
 
You can use tools like gnomeradio, kradio, fmtools, xfce4-radio (plugin for xfce panel), mplayer for listening to the radio.

---

### Post by TheExplorer on 2009-05-30
I'm too having the same AverMedia USB-stick Radio and there is a problem under Ubuntu 9.04 Jaunty.

Well, the problem is that it's not a FM-tuner card, it's just a USB device. So:

1) the program Amusbradio gives an error: did not found 'AVerMedia USB Radio'.
Well, it IS in the system when typing **lsusb**:
Bus 002 Device 004: ID 07ca:b800 AVerMedia Technologies, Inc.

Under Ubuntu 8.10 I used to do:
sudo chmod 777 /dev/usb/hiddev*

But under Jaunty there is simply no such device :(

2) Gnomeradio gives an error: Could not open device "/dev/radio".

Could someone point the appropriate file in /dev to make it work or a fix for that?

---

### Post by TheExplorer on 2009-05-31
Please, someone?

---

### Post by Alexey Klimov on 2009-05-31
> I'm too having the same AverMedia USB-stick Radio and there is a problem under Ubuntu 9.04 Jaunty.

Well, the problem is that it's not a FM-tuner card, it's just a USB device.To be honest it's USB FM-tuner card. This is depend how kernel provide interface in kernel space to this device ;-)

> So:

1) the program Amusbradio gives an error: did not found 'AVerMedia USB Radio'.
Well, it IS in the system when typing **lsusb**:
Bus 002 Device 004: ID 07ca:b800 AVerMedia Technologies, Inc.

Under Ubuntu 8.10 I used to do:
sudo chmod 777 /dev/usb/hiddev*

But under Jaunty there is simply no such device :(Try gnomeradio, fmtools, mplayer, kradio.

> 2) Gnomeradio gives an error: Could not open device "/dev/radio".

Could someone point the appropriate file in /dev to make it work or a fix for that?You should set right file in gnomeradio settings. After plug device, try to find /dev/radio0 file and set this file in gnomeradio.

---

### Post by TheExplorer on 2009-05-31
[quote=Alexey Klimov]
Try gnomeradio, fmtools, mplayer, kradio.
You should set right file in gnomeradio settings. After plug device, try to find /dev/radio0 file and set this file in gnomeradio.[/quote]

Thank you. It works. Seems that it doesn't want to be 'hotplugged'. I had to restart the PC with USB Radio being plugged. That is all.

One more thing...

I had to change privileges a bit:

**sudo chmod 777 /dev/radio0**

After that I could successfully use Gnomeradio :)

**P.S.** It can be a bit irritating to **chmod** every time, so you may add yourself to the **audio** group. That's all.

---


---
title: "Genius Eye Webcam -- colour problem?"
date: 2008-05-05
forum: Multimedia Software
---

### Post by Aleksandar_M on 2008-05-05
I have Genius Eye Webcam. I have problem with picture quality. The picture doesn't have all colors, everything is blue.

---

### Post by linuxwizard on 2008-05-05
Which application or program are you using with your webcam ? If you are using Camorama > Open Camorama > In the white box under effects > right click > add filter > color correction.

---

### Post by Aleksandar_M on 2008-05-06
I try it, but... it's too dark... I am near to the window and I can hardly see my face. I tried contrast/brightness/white balance... nothing helps...

I also noticed that the pc recognized my camera as "Sweex SIF WebCam" not as Genius Eye Cam...

---

### Post by linuxwizard on 2008-05-06
Did you install a driver or did the webcam just work out of the box ? Post the results of the command > lsusb

---

### Post by Aleksandar_M on 2008-05-07
I didn't install anything I just plug in my cam, and I get this...

```
aleks@kubuntu:~$ lsusb
.....
Bus 002 Device 003: ID 04fc:0005 Sunplus Technology Co., Ltd
.....

```
```
aleks@kubuntu:~$ lsusb -d 04fc:0005 -v

Bus 002 Device 003: ID 04fc:0005 Sunplus Technology Co., Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x04fc Sunplus Technology Co., Ltd
  idProduct          0x0005
  bcdDevice            1.01
  iManufacturer           0
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
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
          wDescriptorLength      72
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10

```

---

### Post by linuxwizard on 2008-05-07
Is Camorama the only app. you have tried to use ? Try Kopete or Ekiga and see if you get a better picture. Or maybe that is the best picture you will get in Linux with that webcam & driver. Some webcams just works better in Linux than others.

---


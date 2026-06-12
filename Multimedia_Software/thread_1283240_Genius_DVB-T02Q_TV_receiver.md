---
title: "Genius DVB-T02Q TV receiver"
date: 2009-10-05
forum: Multimedia Software
---

### Post by bixejo on 2009-10-05
Hello all,

After searching through these fora and the Internet I'm close to the conclusion that this TV receiver is almost impossible to make work in Ubuntu, though I'd like to know from those of you that have ever tried to make it work.

Here I drop the output of lsusb and dmesg when I plug this device:

lsusb:
```

Bus 001 Device 004: ID 0458:7040 KYE Systems Corp. (Mouse Systems) 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x7040 
  bcdDevice            0.01
  iManufacturer           1 Genius
  iProduct                2 DVB-T02Q MCE
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           50
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
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
        bInterval               7
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
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
Device Status:     0x0001
  Self Powered
```dmesg:
```
[  175.724018] usb 1-5: new high speed USB device using ehci_hcd and address 3
[  175.857320] usb 1-5: configuration #1 chosen from 1 choice
[  175.948875] usbcore: registered new interface driver hiddev
[  175.949605] input: Genius DVB-T02Q MCE as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[  175.976114] generic-usb 0003:0458:7040.0001: input,hidraw0: USB HID v1.11 Keyboard [Genius DVB-T02Q MCE] on usb-0000:00:1d.7-5/input0
[  175.976140] usbcore: registered new interface driver usbhid
[  175.976144] usbhid: v2.6:USB HID core driver

```I'm trying to make it work in a Jaunty 32bit gnome Ubuntu.

Any reply or comment shall be highly appreciated, though it's just to say that this' not possible to be solved, or relating some (un)successful attempt to solve this.

Many thanks,

---

### Post by valentt on 2010-01-09
Hi, I have the same TV Tuner... did you manage to get you working?

---

### Post by bixejo on 2010-01-09
Nope. Sorry, mate.

From what I've been reading around these forums and the Internet, I reached to the conclusion that there's no way to make it work.

If you eventually get it working, I'll highly appreciate if you'd be so nice to share your info.

Regards,

---

### Post by valentt on 2010-01-09
I tried using it on Ubuntu and Fedora without success.

Here is the info that I get via dmesg and lsusb:

# dmesg 
usb 1-6: new high speed USB device using ehci_hcd and address 8
usb 1-6: New USB device found, idVendor=0458, idProduct=400f
usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-6: Product: DVB-T02Q MCE
usb 1-6: Manufacturer: Genius
usb 1-6: configuration #1 chosen from 1 choice
input: Genius DVB-T02Q MCE as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input14
generic-usb 0003:0458:400F.0007: input,hidraw3: USB HID v1.11 Keyboard [Genius DVB-T02Q MCE] on usb-0000:00:1d.7-6/input0

Is the correct driver for this device dvb-usb-m920x ?

On Fedora 12 with 2.6.31.9-174.fc12.i686 kernel I don't see that this module is getting loaded, and also on Ubuntu...

I manually loaded dvb-usb-m920x module:
# modprobe dvb-usb-m920x
# dmesg
usbcore: registered new interface driver dvb_usb_m920x

I don't see /dev/dvb or /dev/video0 devices present, so I guess that something still is not ok, maybe firmware?

Which is the correct firmware for this device? I downloaded all firmware from: [http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/) and copied them to /lib/firmware and tried reloading the module, still nothing :(

Then I saw post on linux-dvb mailing list saying that correct firware is dvb-usb-megasky-02.fw so I downloaded it also, but still nothing.

That is what I have managed to dig up until now...

Cheers!


-- 
pratite me na twitteru - [www.twitter.com/valentt](www.twitter.com/valentt)
[http://kernelreloaded.blog385.com/](http://kernelreloaded.blog385.com/)
linux, blog, anime, spirituality, windsurf, wireless
registered as user #367004 with the Linux Counter, [http://counter.li.org](http://counter.li.org).
ICQ: 2125241, Skype: valent.turkovic

---

### Post by xc3RnbFO8P on 2010-01-09
Read this:
[http://www.linuxtv.org/pipermail/linux-dvb/2008-April/025660.html]("http://www.linuxtv.org/pipermail/linux-dvb/2008-April/025660.html")

---

### Post by valentt on 2010-01-10
> **Ringi said:**
> Read this:
[http://www.linuxtv.org/pipermail/linux-dvb/2008-April/025660.html]("http://www.linuxtv.org/pipermail/linux-dvb/2008-April/025660.html")

Thanks for the link!

I have one question, as this was the post from 2008 I can only logically assume that there is no need to download code as suggested by mail you linked to. By now the patch should be applied to kernel, no?

I'll mail the mainainer of the driver and ask him directly.

Thanks you once more.

ps. I also sent mail to linuxtv-org mailing list:
[http://www.linuxtv.org/pipermail/linux-dvb/2010-January/032555.html](http://www.linuxtv.org/pipermail/linux-dvb/2010-January/032555.html)

---


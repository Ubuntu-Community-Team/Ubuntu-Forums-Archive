---
title: "Asus U3000 USB DVB Adapter - Help!"
date: 2008-10-19
forum: Multimedia Software
---

### Post by Offramp on 2008-10-19
Hi all,

I am a relative newcomer to ubuntu and I have been trying very hard to get the subject TV tuner working on my own.  I think that I have may have bitten off more than I can chew as a lot of it is going over my head. There are many pages, although I think a lot are aimed at the more advanced user.

The first thing I have noticed is that my device ID is different to that identified at [linuxtv]("http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_Mini").  Would this mean that when the device is plugged in the incorrect driver would be used.  At this [bug site]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/95277"), there is mentioned of changing the device id in one of the header files and the recompiling - but I don't know if I am ready for this yet.  My log files indicate that the device is being recognised, but it looks like it is being recognised as a keyboard?

```

Oct 19 21:20:41 rob-laptop kernel: [ 1304.307469] usb 7-1: new high speed USB device using ehci_hcd and address 8
Oct 19 21:20:41 rob-laptop kernel: [ 1304.338937] usb 7-1: configuration #1 chosen from 1 choice
Oct 19 21:20:51 rob-laptop kernel: [ 1306.864941] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: timeout initializing reports
Oct 19 21:20:51 rob-laptop kernel: [ 1306.865178] input: ASUS  U3000  as /devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.1/input/input17
Oct 19 21:20:51 rob-laptop kernel: [ 1306.901399] input,hiddev96,hidraw2: USB HID v1.11 Keyboard [ASUS  U3000 ] on usb-0000:00:1d.7-1

```


Any help anyone can provide would be appreciated. even just pointers as I would love to get it going myself.

Cheers

---


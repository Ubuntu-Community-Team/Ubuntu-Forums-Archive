---
title: "USB DVB-T mythtv can't open card"
date: 2009-12-11
forum: Multimedia Software
---

### Post by Thameslink on 2009-12-11
Hi
I've put a fresh mythbuntu 9.10 install on my old desktop to try and get it doing something useful.
I can't configure the usb dvb-t stick.
It's listed as an Afatech device under lsusb and restricted-manager has a driver for it but it wont work.
alot of searching has turned up the following
> 
Hi,

I have just recently acquired a new DVB stick device PEAK 202344AGPK (See
[http://www.amazon.co.uk/PEAK-DVB-T-D.../dp/B0010KI5SI](http://www.amazon.co.uk/PEAK-DVB-T-D.../dp/B0010KI5SI)).

This device is an Afatech based device, and marked on the PCB it has DVB-T
395U Rev D. This device seems to have the same PCB as the K-World DVB-T 395U
which is a supported device, but it has a different USB ID (1b80:e395) to
the K-World device.

By modifying the value of USB_PID_KWORLD_399U to 0xe395 in the file
dvb-usb-ids.h the device seems to work well with MythTV, although the remote
control does not seem to be recognised.

Would it be possible for somebody to add in to the code support for this
device ? I'd be happy to do some testing and confirm operation.

Thanks

Mark

--
video4linux-list mailing list

But I can't find the file mentioned.
And do I change where it says 399U to 0xe395 or replace the whole line
I can find /DEV/DVB/ADAPTER0.

Many Thanks

---


---
title: "real dvb-t plus from NPG not working"
date: 2010-12-27
forum: Multimedia Software
---

### Post by Awareness on 2010-12-27
Hi!

I installed linux-firmware-nonfree which I think contains the firmware. I dont know if I have to do anything else because when I open me-tv it says no dvb device connected.


$ lsusb 
Bus 001 Device 006: ID 1f4d:b803 G-Tek Electronics Group Lifeview LV5TDLX DVB-T [RTL2832U]

when i connect the usb stick

$ dmesg
[ 2753.176072] usb 1-6: new high speed USB device using ehci_hcd and address 6

Can anyone help me with this?

Thank you

---

### Post by BicyclerBoy on 2010-12-28
Have you checked LinuxTV v4l (video for linux) website for supported hardware..

It is better to check first then shop.

Don't give your money to vendors that don't work..

---

### Post by xc3RnbFO8P on 2010-12-29
Found this: [http://www.ubuntu-es.org/node/123739]("http://www.ubuntu-es.org/node/123739")

---

### Post by BicyclerBoy on 2010-12-31
Do you know how to proceed ?

So you need to get the video 4 linux source code, think they have moved to git.
That link indicates that only some simple code changes are required.

There will be a lot of dependencies (kernel headers etc) & build tools needed.
There should be a build/install guide with the source code.

[https://bugs.launchpad.net/ubuntu/+source/me-tv/+bug/478379](https://bugs.launchpad.net/ubuntu/+source/me-tv/+bug/478379)

---


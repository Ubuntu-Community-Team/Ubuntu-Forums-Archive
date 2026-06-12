---
title: "Mobile Network Sharing from N95 to Ubuntu 9.10"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by n_s_simpson on 2009-10-31
Hi

I have seen a few people mention that since upgrading from 9.0.4 to 9.10 getting internet through a phone using ttyACM0 doesn't work properly. Here are my findings (and I have all available updates):

When already fully booted up when I connect my N95 via USB and select the PC Suite nothing happens in Ubuntu. It no longer detects it and says I've can connect to the internet using the Mobile Broadband option.

However, when I set my phone to always connect via PC Suite (rather than it asking me how to connect when the USB cable is inserted) and then boot up my computer whilst the phone is connected when I log in to Ubuntu the option is there!

It seems to only give me the option when my phone is connected at initial startup. Is Ubuntu not loading certain drivers unless the phone is connected at boot up? Is this to speed up boot up?

Obviously this needs fixing.

---

### Post by n_s_simpson on 2009-10-31
I have noticed that when first booting up into Ubuntu with the phone connected it sets itself up on ttyACM0. When unplugging it and plugging it back in it sets itself up on ttyACM1.

Not sure if that's the cause.

I did actually plug it in once after Ubuntu had booted up and it did allow me to connect. I have no idea why it did it and I can't get it to do it again.

Has anyone got a fix for this? I don't have broadband so constantly having to reboot Ubuntu is driving me potty. Thanks.

P.S.

Apart from this Ubuntu 9.10 is far better than 9.0.4 :D

---

### Post by n_s_simpson on 2009-10-31
UPDATE:

**When booting up Ubuntu 9.10 with N95 plugged in and set to PC Suite:**
An internet connection is established using ttyACM0

**When unplugging phone after connection established and plugging it back in:**
No internet connection.
When typing dmesg it mentions ttyACM1 is there.

**When plugging phone in after boot-up (not plugged in whilst booting up):**
No internet connection.
When typing dmesg there's no mention of ttyACM (ttyACM0 or ttyACM1) and all it says is:
[  313.944015] usb 5-2: new full speed USB device using uhci_hcd and address 3
[  314.118434] usb 5-2: configuration #1 chosen from 1 choice

So I'm totally lost now.

---

### Post by n_s_simpson on 2009-10-31
UPDATE 2:

Assuming I have booted up Ubuntu with the phone connected so the internet is available and phone is set up on ttyACM0:

If I click on the network status icon and then select disconnect, when I unplug the phone and reconnect it the network can be re-established and it sets itself on ttyACM0.

However, If it's connected on ttyACM0 and I unplug the phone without disconnecting first when I plug it back in the connect option is no longer there.

When typing dmesg what I see is:

[ 1678.668016] usb 5-2: new full speed USB device using uhci_hcd and address 6
[ 1678.842943] usb 5-2: configuration #1 chosen from 1 choice
[ 1678.874868] cdc_acm 5-2:1.10: ttyACM1: USB ACM device
[ 1678.881063] usb 5-2: bad CDC descriptors
[ 1678.886857] usb 5-2: bad CDC descriptors


So to recap I have to have the phone connected while Ubuntu 9.10 is booting. If I do not select disconnect before unplugging it (or if you accidentally unplug it) I have to reboot my computer.

Here is a log from typing dmesg when I was testing the above for anyone out there that can work out what's going on:

[ 1425.424042] usb 5-2: USB disconnect, address 2
[ 1437.452017] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 1437.630148] usb 5-2: configuration #1 chosen from 1 choice
[ 1437.662118] cdc_acm 5-2:1.10: ttyACM0: USB ACM device
[ 1437.668067] usb 5-2: bad CDC descriptors
[ 1437.668599] usb 5-2: bad CDC descriptors
[ 1556.120044] usb 5-2: USB disconnect, address 3
[ 1562.756019] usb 5-2: new full speed USB device using uhci_hcd and address 4
[ 1562.930932] usb 5-2: configuration #1 chosen from 1 choice
[ 1562.960913] cdc_acm 5-2:1.10: ttyACM0: USB ACM device
[ 1562.967857] usb 5-2: bad CDC descriptors
[ 1562.967957] usb 5-2: bad CDC descriptors
[ 1573.232044] usb 5-2: USB disconnect, address 4
[ 1581.072018] usb 5-2: new full speed USB device using uhci_hcd and address 5
[ 1581.246936] usb 5-2: configuration #1 chosen from 1 choice
[ 1581.280875] cdc_acm 5-2:1.10: ttyACM0: USB ACM device
[ 1581.286875] usb 5-2: bad CDC descriptors
[ 1581.287003] usb 5-2: bad CDC descriptors
[ 1630.024044] usb 5-2: USB disconnect, address 5
[ 1678.668016] usb 5-2: new full speed USB device using uhci_hcd and address 6
[ 1678.842943] usb 5-2: configuration #1 chosen from 1 choice
[ 1678.874868] cdc_acm 5-2:1.10: ttyACM1: USB ACM device
[ 1678.881063] usb 5-2: bad CDC descriptors
[ 1678.886857] usb 5-2: bad CDC descriptors
[ 1931.517049] usb 5-2: USB disconnect, address 6
[ 1931.788015] usb 5-2: new full speed USB device using uhci_hcd and address 7
[ 1931.962630] usb 5-2: configuration #1 chosen from 1 choice
[ 1931.993586] cdc_acm 5-2:1.10: ttyACM1: USB ACM device
[ 1932.000633] usb 5-2: bad CDC descriptors
[ 1932.005819] usb 5-2: bad CDC descriptors
[ 1934.049539] usb 5-2: USB disconnect, address 7

---

### Post by 3esmit on 2009-10-31
Hello n_s_simpson.

I think this is an kernel bug. I've posted a bug in launchpad site, take a look, and contribute with information that could help tracking the source problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/466045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/466045)

There is also another person that just registred exaclty your problem, take a look:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369190](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369190)

Don't forget to mark as affecting you ;)

Thank you for sharing your problems.

---

### Post by zkam83 on 2009-11-17
I've been struggling with this since ubuntu 9.10 beta. I have a USB ISDN modem and every few minutes it disconnects (crappy ISPs) and I have to run pppconfig and change the device from ttyACM(x) to ttyACM(x+1). Does anybody know of a work around?

---

### Post by mikeh on 2009-12-12
> **zkam83 said:**
> I Does anybody know of a work around?

You can pass the device name as an argument to 'pon' etc and over-ride the config file. Need to be root to over-ride of course. e.g.

$ sudo pon myisp /dev/ttyACM6

Or in a script:

> pon myisp `ls /dev/ttyACM*|tail -1`

---


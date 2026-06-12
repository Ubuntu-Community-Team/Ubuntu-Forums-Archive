---
title: "Any software for Soft AP?"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by darkod on 2009-11-30
Hello.
I am running Karmic Desktop 64bit. I am expecting a USB wi-fi adapter and would like to share my dekstop ethernet internet with my netbook (integrated wi-fi).
I have tried with another usb wi-fi and I know ad-hoc is rather simple. In fact, as soon as it was plugged in and I created new wireless network, it worked. Didn't even have to specify internet sharing anywhere. Impressive...
But with this new usb wi-fi I would like to set it up more like Soft AP. I think it would support that because the software on the CD includes it for windows. Can't try until it gets here but I don't hope it will have software for linux too.
So is there any straightforward software I can use to create Soft AP? Doesn't have to be GUI, as long as setting up is not that complicated. Maybe some tweaks with the interfaces can work even without specific software?
I was googling for a while but didn't find anything specific except this:
[http://ubuntu-tutorials.blogspot.com/2007/02/enable-wpa-wireless-access-point-in.html](http://ubuntu-tutorials.blogspot.com/2007/02/enable-wpa-wireless-access-point-in.html)
Thanks in advance for any help.

---

### Post by darkod on 2009-11-30
I did some more reading and it seems you can set master mode with
iwconfig wlan0 mode master

Of course, if the device and driver allow it. Would that be all that's needed? And after I use the standard process trough Network Manager and create wireless network?
Does the above command make the master mode permanent or until reboot?

---


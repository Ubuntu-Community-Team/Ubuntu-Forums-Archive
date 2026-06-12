---
title: "Wifi Dongle Driver Problem"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by davehal on 2010-09-25
Hello

I have just installed Ubuntu on an old laptop for a little bit of programming and to gain some familiarity with linux. Im looking forward to getting to know my way around the OS :)
Unfortunately, the wireless card (for wifi) on this laptop is broken, so instead I have been using a wifi usb dongle on windows. I am having some trouble installing this dongle in ubuntu, i cant find a driver for it!
Its a "MicroNext MN-WD546J 54M Wireless Adapter"
[http://cpc.farnell.com/1/1/66310-adaptor-usb-wireless-bg-mn-wd546j-micronext.html](http://cpc.farnell.com/1/1/66310-adaptor-usb-wireless-bg-mn-wd546j-micronext.html)

I have my modem connected directly at the moment via LAN, and this works no problem, but id like to get it connected wirelessly

Can anyone help??

Thanks

Dave

---

### Post by booah on 2010-09-25
Dave,
try going to synaptic poacket manager and downloading "ndiswrapper" (it will include 2 more packages). apply than and let it install. Then go System->admin->windows wireless drivers and go install new driver. You will need to find the .inf file on the driver cd for your wireless usb then click ok. That should be it, make sure to have wireless enabled

---


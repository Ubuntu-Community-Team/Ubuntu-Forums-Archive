---
title: "NDISwrapper &amp; FWcutter"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by gibbylinks on 2009-05-25
Hi All,

I was using NDIS wrapper with the windows driver for my Broadcom 4318 wireless adapter and it was decidely flaky. It connected but not all the time.

I've now installed FWCutter and removed the windows driver, and so far it's working.

My question is do I still need NDISwrapper or is FWCutter something different.

Could someone explain for me what these two packages do, and enlighten me.

Cheers

---

### Post by t0mppa on 2009-05-25
NDISWrapper uses the Windows drivers to configure your interface. Doesn't need any other modules to get things up and running.

FWcutter "cuts" the firmware (FW) that's required to be loaded to your interface in order for it to work and is used in conjunction with b43 drivers. The firmware alone will not get your device working, you'll still need drivers on your OS to get the device up, so FWcutter alone won't do any good.

You can open up a terminal and enter 'lshw -C network' into it. From the output that command gives you will find your wireless interface and it will also tell which driver is managing it. If NDISWrapper isn't mentioned and your interface works, then you can remove NDISWrapper completely from your system.

---

### Post by gibbylinks on 2009-05-25
Thanks for swift reply. I doesn't mention ndiswrapper, also I now have the driver listed under hardware.

I'll leave it for now and see how it goes. It appears to be working better than ndiswrapper but I'll wait and see

:D

---

### Post by t0mppa on 2009-05-25
Yeah, I recently swapped over from ndiswrapper myself. Hopefully this tiresome tinkering with wlan is over now.

---


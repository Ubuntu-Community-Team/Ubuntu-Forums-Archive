---
title: "some progress with wifi"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by dcast on 2006-02-19
I was having issues with ndiswrapper and those have been resolved so now when i click configure network in ndisgtk my usb adapter is not recognized in networking, so I cannot configure my network although ndis says that I have the driver isntalled and the hardware is present. Can anyone help me?

---

### Post by Lambert on 2006-02-19
according to ndis you have a driver installed which matches the device but it is not a working driver which is why you don't see it in the networking screen.

Two things I can think of quickly.

1. Do you have the .sys file installed also. You can check /etc/ndiswrapper/(drivername)/
It should be listed in that directory.

2. You need to use a different driver then the one you're using. It may be a windows driver for the device, but it doesn't work with ndiswrapper. You have to fish around for another driver for the device. check ndiswrapper wiki to see if a verified driver is listed for your device. Make sure you remove the first one with ndiswrapper -e before installing a new driver

---

### Post by dcast on 2006-02-19
For hte first one I have the right stuff isntalled. I will go on a hunt for a different driver. Thanks for your help.

---


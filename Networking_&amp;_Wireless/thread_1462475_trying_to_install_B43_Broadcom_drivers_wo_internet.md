---
title: "trying to install B43 Broadcom drivers w/o internet connection"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by thisguykills on 2010-04-25
I have a netbook that I installed ubuntu 10.4 on via live usb. It informed me when I installed that my broadcom wireless driver needed an update. I followed the guide here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access)

under the USB/Netbook section. I installed all the things that it told me to, but once I tried going to the hardware drivers app, it told me that no proprietary drivers were in use. Basically I need to know how I can install the updates to my wireless driver, without internet and/or what I did wrong the first time.

My ethernet controller is NetXtreme BCM5751. It told me I needed the B43 broadcom update if that helps at all. Thanks a bunch.

---

### Post by themrfox on 2010-04-25
This helped me: don't install ubuntu yet have it take you to the "Test" mode from there you need to check your hardware drivers it'll come up with the drivers your looking for enable them and your wireless will come up but won't work...yet. From there install Ubuntu onto your computer after installation is complete navigate back to the hardware drivers and enable the driver it still doesn't work at this point. Right click your installation medium for Ubuntu and open with archive manager from there navigate through /pool/restricted/b there you will find one package install it go back to hardware drivers and enable it then restart your computer everything should be peachy

Hope this helps

---

### Post by thisguykills on 2010-04-25
When I click activate, it says the driver failed to install.

EDIT: Never mind I found out how to do it. I connected my netbook directly to the router and now it works. Thanks!

---

### Post by dogeatery on 2010-08-24
> **themrfox said:**
> This helped me: don't install ubuntu yet have it take you to the "Test" mode from there you need to check your hardware drivers it'll come up with the drivers your looking for enable them and your wireless will come up but won't work...yet. From there install Ubuntu onto your computer after installation is complete navigate back to the hardware drivers and enable the driver it still doesn't work at this point. Right click your installation medium for Ubuntu and open with archive manager from there navigate through /pool/restricted/b there you will find one package install it go back to hardware drivers and enable it then restart your computer everything should be peachy



<p>I attempted this very thing while running a persistent live USB, but the archive manager said it couldn't read the .iso image.  What gives? </p>

<p>I've also installed the broadcom drivers manually from a .deb package but they go unrecognized by my system.  Am I doing something wrong?</p>

<p>Does it have anything to do with the fact that it's from a live USB?  I wanted to try out the distro before installing it.</p>

---


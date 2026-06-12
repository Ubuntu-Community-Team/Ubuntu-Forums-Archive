---
title: "New to Ubuntu - Wireless Card Not Showing Up"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Jweitz on 2009-10-31
Hello,

I am new to Ubuntu and this is the first version of Linux that I have tried. Everything in the install seemed to go well. Everything is working so far except my wireless network connection. I am using a HP 6735s with a broadcom wireless network adapter. I have tried some of the solutions in the other threads, but they all seem to be for connectivity issues, not for teh card not showing up. I am using version 9.10. Any help would be appreciated.

---

### Post by Immolatus on 2009-10-31
I'm running 9.10 on a Dell with the broadcom card and I had to do this like I did a couple years ago when there was very little "out of the box support" for wifi with Linux.
Firstly, go here:  [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3687622&prodTypeId=321957&prodSeriesId=3687621&swLang=13&taskId=135&swEnvOID=1093#11395](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3687622&prodTypeId=321957&prodSeriesId=3687621&swLang=13&taskId=135&swEnvOID=1093#11395)

It is the exact location of the driver for your wifi card. As far as I know you need the XP driver to work with ndiswrapper so download that one and put it on a usb key (make sure you save it there, you never know when you might need it again).

In your "home" folder create a folder called "wireless" or whatever you want to call it. Drop a copy of the driver in there and extract it there as well --> right click --> extract here.

Open synaptic package manager and install ndiswrapper, just use the search option it'll be a short list.

Restart machine.

Go to System --> administration --> windows wireless drivers.

I'm sure it's pretty obvious from there but restart again after installing the driver.

P.S. some people are saying to install the  bcmwl5 kernel source but I don't think you need to, I think it's all ready there, mine was. If not try it.

---

### Post by Jweitz on 2009-10-31
When I download the driver from the hp website, it get an exe which i cant extract or open. Is there anywhere I can just get the driver without hp's installer?

---

### Post by Jweitz on 2009-10-31
Ok, I got the drivers installed, and it says they are working, but nothing is showing up as far as wireless networks

---

### Post by Jweitz on 2009-10-31
Never mind, I finally got it working. Thanks for the help.

---


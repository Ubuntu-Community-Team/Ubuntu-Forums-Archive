---
title: "Problems getting WMP54G working with ndiswrapper"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by shaun680 on 2006-01-20
I'm using Ubuntu 5.0.4 (Hoary) for amd64. My wireless card is a Linksys WMP54G (not sure which version and I don't know how to find out, but I am 99% sure that it uses the Broadcom chipset). I followed the instructions [here](https://wiki.ubuntu.com/HowtoUseNdiswrapperOnAmd64Ubuntu) to get Ndiswrapper (1.18) installed and everything seemed to go fine, no errors etc and when I type ndiswrapper -l it says the driver is loaded and the hardware is present. But in system -> admin -> networking the card should be there, and its not. I assume then that it is a problem with the driver, not ndiswrapper.

The driver I am using is the Linksys WMP54G one from [this](http://www.linuxant.com/driverloader/drivers.php) site as recommended in the wiki article. Is that the right driver, or do I need the generic 64bit one at the top of that page? Does anyone know what I can do to get it working this way, or tell me another way without using ndiswrapper (that is free)?

---

### Post by shaun680 on 2006-01-20
OK, so I used a different driver, and now wlan0 is showing up in the networking page. But when configuring the properties for it, I found nothing for WPA, only a box to put in the WEP key. I tried putting my WPA key in the box for WEP, and it did activate after a little while of trying, but no webpages will load. What do I do now to get WPA working?

---


---
title: "ATI driver problem with 11.04"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ez1to3 on 2011-03-06
Hey, so I've looked all over the internet for a solution, and cannot seem to find one. When i boot 11.04 just a blank screen displays. I figured that the driver was not working correctly, so In recover mode I tried every which way to install the driver. tried fglrx as well as the driver from the ATI site. The closest I've gotten is a purple screen with the Ubuntu logo appearing, unfortunately it goes back to the black screen. I uninstalled the driver and tried rebooting, and this time is sent me to the recovery by itself. the driver does not load in "Additional Drivers" and there are no other options i can think of. Please help!
My card is HD 5450.

---

### Post by Harry33 on 2011-03-07
> **ez1to3 said:**
> Hey, so I've looked all over the internet for a solution, and cannot seem to find one. When i boot 11.04 just a blank screen displays. I figured that the driver was not working correctly, so In recover mode I tried every which way to install the driver. tried fglrx as well as the driver from the ATI site. The closest I've gotten is a purple screen with the Ubuntu logo appearing, unfortunately it goes back to the black screen. I uninstalled the driver and tried rebooting, and this time is sent me to the recovery by itself. the driver does not load in "Additional Drivers" and there are no other options i can think of. Please help!
My card is HD 5450.

The driver you are trying to install (fglrx) is AMD/ATI's proprieatary driver.
Unfortunately it does not yet support the newest xserver (1.10) in Natty.
Ubuntu community cannot change that, only AMD/ATI can do that.

But there is available the open source driver which should work also with the ATI radeon hd5*** series.

Check that you have installed these:
- xserver-xorg-video-ati
- xserver-xorg-video-radeon

Then remove this file (if it exists):
- /etc/X11/xorg.conf

Also check that this file is not installed:
- fglrx

---


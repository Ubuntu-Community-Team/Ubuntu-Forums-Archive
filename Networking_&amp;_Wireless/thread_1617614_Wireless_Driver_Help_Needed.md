---
title: "Wireless Driver Help Needed"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by syrius013 on 2010-11-09
Earlier today my Wireless was working perfectly. I shut my a laptop down for a moment to switch classes. When I started it up, My wireless had autoed to disable my wifi, when I enabled it, it couldnt find any connections. I checked my Drivers and I noticed I have a new driver. I have been using the Broadcom STA wireless driver, but now I have a Broadcom B43 wireless driver, both inactive. I went to activate either one, and it says it cant fetch it. I know this is because I have no connection. I have 10.04 on usb and went to re-download the STA driver, but it says its already installed. When I went to reinstall, it says: An unhandlable error occurred: There seems to be a programming error in aptdaemon. I have read [http://ww.ubuntuforums.org/showthread.php?t=1604868](http://ww.ubuntuforums.org/showthread.php?t=1604868), but I dont have internet. I do however have a wired desktop, and a usb, so I can transfer files if need be. Is there anyway to download the correct drivers through usb?

---

### Post by syrius013 on 2010-11-10
Lol, I dont know why I post to this forum. I end up solving my own problems. I found out that when I closed my laptop, that it did not shut down all the way, causing it to hibernate. Ubuntu then soft blocked my wireless in an attempt to save power. I found this out by using. 

rfkill list

I fixed this by using the command:

rfkill unblock all.

Fixed! :)

---


---
title: "Wifi not connecting after update"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by Ergo0100 on 2011-03-02
Hi everyone!

i have recently built a computer for my room and installed ubuntu 8.X (don't remember the number right now). My idea was to use a very old usb wifi card (it's a Encore ENWLI-USB1-NT/A). I booted the first time with ethernet connected. i connected my usb wifi card and ubuntu automatically downloaded drivers for it (atmel *something*). Then i disconnected ethernet and connected to the router with a WEP password. It all worked awesome... until now. I got an update window an it said that there was a new version of the system (9.10). So i upgraded it.

After the reboot the wifi card was recognized but didn't wanted to connect to the router. It asked me for the password of the wifi and tried to connect. after 2 minutes it couldn't connect and asked me the password (i'm 100% sure it's the correct password). I thought "must be the drivers. Something happened with the update" so i installed ndiswrapper via ethernet and searched the drivers CD. I used the Windows XP drivers and installed both inf that were in the folder. Then i rebooted with ethernet AND wifi card unplugged. Then i connected the wifi card and opened ndiswrapper. I got an error saying something like "could not determine if device is connected". I clicked ok and saw that one of the two inf was showinh "hardware connected: yes".

Meanwhile, i did't noticed that ubuntu tried to connect automatically to the router. I thought "cool! now it should work with the windows drivers". nah. It keeps showing the password screen again and again...

I couldn't find updated drivers. I searched over 30 websites and didn't find any download. Not even in the encore website. 

Please im VERY VERY new in linux so i don't know many essential thing like using the terminal.

I don't want to live using the ethernet cable. It goes from the entrance of my house to my room and goes through all the corridor.

---

### Post by nssone on 2011-03-02
I am having a similar issue, possibly very related. I just ran an update less than an hour ago and now I can't seem to connect to wifi or even ethernet. The wireless was acting just fine until I ran an update and rebooted. 

I can't think of any other possible causes for this other than the update messed something up. It's not hardware because I am typing from from a LiveUSB of 10.10 with my USB wifi dongle manually installed onto it. Anybody have any idea on what it could possibly or some way to rollback to get this to work again?

---


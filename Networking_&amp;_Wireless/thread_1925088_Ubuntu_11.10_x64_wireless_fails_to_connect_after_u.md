---
title: "Ubuntu 11.10 x64 wireless fails to connect after update"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by GMS1 on 2012-02-13
After my 11.10 did a software update last friday my Linksys WMP600N fails to connect to my network. It recognizes the card properly as well as the drivers. I can access the network I am trying to connect to in the Network Manager but after selecting connect it just won't connect. I know the card is funtional because I checked it in another working Windows computer and it works fine. Also the network is functional because there are three other computers that are connected and working fine.

---

### Post by GafftheHorse on 2012-02-15
I just encountered a similar issue after the kernal update today (x64). After reboot wireless just would not connect (a TP-Link 721N usb stick). I tried rebooting to an older kernal to no avail. No matter which network applet i tried or how I tweaked the settings it wouldn't connect from the Network Manager (icon on desktop)

Finally got it working simply by going into Network on System settings (Gnome or Unity) and turning wireless off and on, then selecting my wifi point from the list of available and it connected immediately. Quite a relief after much head-scratching for most of the night.

---

### Post by GMS1 on 2012-02-15
GafftheHorse, thanks for the reply! I actually tried that but mine is not being so nice. At this point I am going to have to write a "ticket" that is explained on the sticky thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) ("Wireless card list and procedure to get help). Thanks again! Take care!

---

### Post by GMS1 on 2012-02-17
To all,
 
This morning I decided to retry resetting the connection in wireless manager to no avail again. I had an idea to reset the modem/router and after it/they had rebooted everything snapped back togather again and is working like it should. I left the Linux systm on with the wireless connection at its "failed to connect state" and when I came back to the system from rebooting the modem/router it had already connected. Thanks again GafftheHorse for the replay. To all, take care!

---


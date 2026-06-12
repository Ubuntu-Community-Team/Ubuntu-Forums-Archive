---
title: "nm-applet and Safe Mode &lt;3"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by ThePonola on 2011-03-27
So, even after learning how to install a driver, tweak it, and learn how to boot the kernel with options.  My WiFi was still hit and miss.  With missing causing a black screen of death.

The driver I installed was for the RaLink 5390, on my Compaq Presario CQ56.

But yeah, I was reading, and reading, and reading about how to fix this problem, when I found out that by logging into Safe Mode, logging out, and then logging in the normal desktop, it would always connect!  I don't have the link to the thread where I found that though...
Anyway, they asked "I wonder what's done differently?"  Another thread said that Safe Mode and then the command "dhclient ra0/eth1/wlan0" worked, but it didn't for me, but going into Safe Mode, then using the command "nm-applet" always brought up Network Manager and used my WiFi perfectly.
Deciding to just log into Safe Mode permanently and have nm-applet auto start, I went to System > Preferences > Startup Applications to add it there.  But it was already there...

It also had an option... --sm-disable.  EUREKA!
I was only using "nm-applet" in Safe Mode, not "nm-applet --sm-disable"!  That's what was different!

So I removed that option, and logged into the normal desktop mode, and now, my wireless works flawlessly everytime. <333

Just wanted to share that, and I hope it comes to help some of you guys.  Hopefully I'm not just some weird exception or something. xD

(Sorry if this is in the wrong place... I'm a newb :<)

---


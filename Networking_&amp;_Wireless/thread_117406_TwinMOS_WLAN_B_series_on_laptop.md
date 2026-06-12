---
title: "TwinMOS WLAN B series on laptop"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by daverd on 2006-01-14
Hi, I've got an IBM Thinkpad with a TwinMOS WLAN B series (B230) card. I successfully followed instructions to install ndiswrapper and the WinXP driver for this card, and ndiswrapper -l tells me both hardware and driver are present, no problems.

However, I can't get it to successfully connect to my wireless router (netgear mr814v2). I know the router works because I have used it with other wireless devices. More annoyingly, having the WLAN card present seems to screw up my eth0 connection until I shut down, remove the WLAN card, and reboot.

I'm not even sure where to begin asking questions about how to fix this or what information to post, etc. I am using the latest version of breezy. Any help?

- David

---

### Post by Zelut on 2006-01-14
I'll take some guesses on things to try:

Do you have the SSID for your router defined in Networking?  (gnome: System > Admin > Networking).  Uhm, also, is your router using any kind of WEP/WPA encryption?  That can cause issues as well unless setup correctly.

I might suggest disabling the eth0 if you plan on using wlan0.  If you're going to use the wireless more often than the wired removing it from the equation could solve the conflict problem.

---

### Post by daverd on 2006-01-15
Yes the SSID is correctly set up and I've had issues whether encryption is on or off on the router.

Anyway I did some messing around and I think I've got a more specific error now...

root@rasputin:/home/daverd# iwpriv wlan0 setkey 1
Interface doesn't accept private ioctl...
setkey (8BE2): Operation not permitted

I did some searching on google for that error  message and nothing useful came up.

- David

---


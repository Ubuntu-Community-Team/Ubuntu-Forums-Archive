---
title: "Authentication required by wireless network - multiple dialogue boxes"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by weiersc on 2011-12-15
Hi,

It's been bothering me since I upgraded to 10.10. My laptop is usually connected to the router through a cable as it is close to the edge of the wireless range with an unreliable signal.

Despite being connected to the wired network I keep getting an authentication box that says: "Authentication required by wireless network."
If I ignore it, a second authentication box will pop up a few minutes later and often when I come back to the laptop after being away for a few hours, there are eight or ten of these authentication boxes open on my screen.

The problem goes away if I manually disable the wireless card, but this is usually only temporary. When I reboot, or when the cat walks on my keyboard it usually comes on automatically again.

Questions:
1. Is there something I can do in my settings to let this connection take place automatically without asking for authentication (the dialogue box already has the correct password in it)?

2. If I have to provide authentication - how can I go about requesting that the system brings only one box and patiently waits for an answer from me, rather than to keep displaying multiple new boxes? (An action on one of the boxes does not cause the other boxes to go away.)

I have not experienced this in earlier versions. I experience this on all my devices.

---

### Post by ajgreeny on 2011-12-15
Right click on the network manager icon in the panel, and go to "Edit Connections" then find the wireless connection, again click on Edit, and make sure both boxes for "Available for all users" and "Connect automatically" are both checked.

---

### Post by weiersc on 2011-12-15
I've just double checked. I have both those boxes checked, but as I'm typing I just got another authentication request. So this does not solve the problem for me.

---

### Post by phord2 on 2013-01-24
The dialog is not requesting local user login; it is requesting network credentials.  

I still get this on 12.12.  It is reportedly fixed in the next release.  See the end of this bug thread:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/912702](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/912702)

Other places where it's been complained about:
[http://askubuntu.com/questions/197078/prevent-duplicate-wireless-authentication-windows](http://askubuntu.com/questions/197078/prevent-duplicate-wireless-authentication-windows)
[http://askubuntu.com/questions/180126/wireless-network-found-cant-connect-repeated-requests-for-authentication](http://askubuntu.com/questions/180126/wireless-network-found-cant-connect-repeated-requests-for-authentication)

---


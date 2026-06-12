---
title: "VNC and Remote Desktop - Problem for the Pros"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by stephanmir on 2011-03-01
Hey guys,
 
 
So earlier the whole community at the ubuntu forums helped me out with fixing this issue. We were able to get everything hooked up and the computers can communicate with each other. Here's what we got so far:
 
Ubuntu home PC w/ Remote Desktop enabled. Had to put an exception to the firewall to allow my laptop to connect to it.
 
Laptop runs Windows 7 UVNC to connect to the home system.
 
**BUT**
 
The connection speed from when I click on the screen to something actually happening is extreeeeeemely slow. I attempted to remedy this by putting in the following command as administrator under the Windows 7 system on my laptop:
 
netsh interface tcp set global autotuninglevel=highlyrestricted
Ok.
 
Alas... no high speed clicky clicky....
 
So what am I doing wrong here?
 
Thanks all!!!
 
-- Stephan
 
I'd be lost without you guys.
 
-----------------------------------------
 
Looks like it's a color issue. The more in depth the colors the longer it takes for things to happen.

---

### Post by stephanmir on 2011-03-01
Ok so since I was able to determine that the full colors make it super slow and I can speed up the connection if I make it reflect 256 colors, is it possible to have it set as full colors on and have it still maintain a high connection speed?
 
Thanks

---

### Post by aeiah on 2011-03-01
sounds like its slow for bandwidth reasons. home networks tend to have a low upload speed compared to download. your server at home only has limited bandwidth to push what are essentially screen captures up to your remote laptop.

why do you want to remotely access your desktop at home? you may find that ssh or a web control panel will suit your needs better

---

### Post by toshko3 on 2011-03-01
I use x11vnc (started with the user, not root user) and all is perfect.:popcorn:

---


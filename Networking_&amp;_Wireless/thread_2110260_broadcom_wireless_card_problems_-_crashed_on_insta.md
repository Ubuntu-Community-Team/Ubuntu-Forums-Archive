---
title: "broadcom wireless card problems - crashed on install"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2013-01-29
I'm just in the process of setting up an ubuntu 12.04 box with some old hardware I had. It's got a broadcom 43 wireless card. At first, when I tried to open the 'additional drivers' section of system settings it just hung, but after a system update it seemed to work properly. The card showed up and I clicked to install it and went away to make a cuppa. When I came back the screen was filled with greyed out text on black and the computer was unresponsive. After a reboot, the card no longer shows up in this section (though my graphics card does) and wireless has even vanished from the drop down network menu...
lspci shows the card is still there, but I'm stuck what to try next... help?!
Thanks!

---

### Post by mistafeesh on 2013-01-30
Here's how the card is identified:

02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Subsystem: Broadcom Corporation Device [14e4:120f]

Is my chipset even supported? It's a fairly old "airport compatible" card for  a mac...

---

### Post by D0wnp0ur on 2013-01-30
This is EXACTLY what is happening to me. My card is also the 4306 8.11b/g. Still waiting on a fix for this issue.

---


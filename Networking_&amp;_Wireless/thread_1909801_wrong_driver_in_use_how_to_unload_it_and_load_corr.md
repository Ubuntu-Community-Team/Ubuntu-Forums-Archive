---
title: "wrong driver in use how to unload it and load correct one"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2012-01-16
I have a Dell Laptop on which wireless is giving me problems.The card some times is detected and some times the card could not be detected.I noticed this problem started since I did suspend and resume of my laptop i.e. close the flap of laptop and then reopen it.It is this time that laptop gets suspended and and resume again.

After this I erased entire Ubuntu 11.10 from my system and did a clean install.
Installed STA driver from the additional drivers section.After this got my wireless  working.But I as soon as I close the flap of laptop and then reopen it again the connectivity goes and > rfkill list command shows 

> rfkill list
0: brcmwl-0: Wireless LAN
	Soft blocked: no
**	Hard blocked: yes**

and then onwards I can not connect to any kind of wireless network.I did not switched off the wifi button as rfkill command above shows Hard blocked.

---


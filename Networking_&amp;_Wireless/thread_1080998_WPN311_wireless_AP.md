---
title: "WPN311 wireless AP"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Tactical Fart on 2009-02-26
I already know that I need madwifi-tools to use this card. (I can connect to my wireless router before installing this but all of the how-tos that I've read called for it.) I read somewhere that I have to be able to run ```
(I'm paraphrasing. I lost the link to the page that has this.)
sudo iwconfig ath0 mode master
``` without getting errors, but I keep getting them anyway. I'm trying to set up a WEP AP that I can open and close remotely through the command line. (I've already got SSH down pat.) I'm aiming for WEP because the computer is wired into the network anyway, plus the router is set for WPA2. if I have the computer act as an AP, then I can connect my DS to it without weakening my security, changing the setting forwards and backwards just to get it online, or disrupting my network (which is mostly wireless). Should I just give up now, or try another approach? (And before you ask, no, the DS does not support anything stronger than WEP, and according to my research, it doesn't like ad-hoc. I've tried it.)

---


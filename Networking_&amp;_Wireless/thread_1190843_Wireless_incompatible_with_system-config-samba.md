---
title: "Wireless incompatible with system-config-samba"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by kircher on 2009-06-18
I have been having trouble with my wireless connection over the past few days, and I believe I have gotten to the bottom of the problem. It seems that having system-config-samba installed interferes somehow, and makes the wireless connection unstable and even impossible to connect. Samba didn't function properly at all over the wireless network either, as I was unable to access my shared files at either end of my network. system-config-samba is a GUI for easy use of samba without having to manually edit the smb.conf file. I have since removed it, as well as libuser1 and python-libuser, which it depends on, and my wireless connection seems to be working perfectly, as well as samba - I guess manually editing smb.conf is not so bad after all.

---


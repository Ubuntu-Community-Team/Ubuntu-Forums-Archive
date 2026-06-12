---
title: "Broadcom STA stopped working"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by sagyvolkov on 2009-05-25
Running 9.04 (Bets install and just kept on updating, so I guess its the latest).
Dell D630 with Broadcom 4312 wireless.
Everything was working fine from the get go, I could use the wireless.
After 4 months of using the laptop, suddenly NetworkManager stop discovering that I even had a wireless card, meaning it would only show the "Enable Networking" not the "Enable Wireless".
I looked in System->Administration->Hardware Drives and saw the STA is there, enabled, but written that it is not in used, so I remove it and installed and then NetworkManager discovered the card and I got wireless to work, the only thing I have to do this after each reboot and most of the times after coming back from suspend.
a few days, another thing started to happen and I can not use wireless in my home anymore. Nothing was changed at my home settings, nor on the laptop itself, it just stopped working. 
attaching a few lines from daemon.log while trying to connect to my home network.

Any help will be appreciated.

---

### Post by sagyvolkov on 2009-05-26
Never mind, friggin Uverse router was the reason, a restart to it fixed this problem.
Please close the thread.

---


---
title: "Atheros Wireless card can see networks but can't connect"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by fr0otlo0p on 2010-05-30
All right, I'm fairly new to Ubuntu & Linux, I've installed it no problems on my desktop and I really love it.  Now I'm trying to install it on my Satellite and I'm having a couple of problems.  When trying to connect to my wireless network, I can see my network, but it will just keep asking me for my WEP.  I've confirmed that there is nothing wrong with the network or the password I've provided.  Sometimes when I boot up, the network manager just says that the wireless networks are disconnected and can't find any.  The wired connection always works just fine.

Here are the system specs that I would consider relevant, but ask me if you need anything else:

Toshiba Satellite M45 S169
Ubuntu 10.04 Lucid Lynx LTS Fresh Install

Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
Kernel driver in use: ath5k
Kernel Modules: ath5k

As always, thank you for your help.

---

### Post by fr0otlo0p on 2010-05-30
Ok, now what I've done is found the window's driver for my card and installed it with ndiswrapper.  I then added ath5k to the blacklist file.  After a reboot, the problem still persists.  Is there anything else I can do?

---

### Post by fr0otlo0p on 2010-05-31
After installing Wicd, I was able to get the wireless working.

---

### Post by mojo706 on 2011-05-21
My card can see other networks but not mine?

---


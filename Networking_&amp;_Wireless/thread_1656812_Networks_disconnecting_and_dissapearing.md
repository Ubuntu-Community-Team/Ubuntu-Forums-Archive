---
title: "Networks disconnecting and dissapearing"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by Papug9 on 2010-12-31
Hey,

I have recently installed ubuntu on my laptop again using wubi.
I have the same network problem as always.
When I connect to a network. About 7 - 10 minutes after connecting I get disconnected from my network. (I also get asked for the WEP/WPA key/passphrase - my home wep is 64-bit).
Then all wireless networks disappear. 
I have an Atheros AR5007EG wireless card, I am using madwifi drivers (it seem to come up with some errors to do with the kernel... :confused:)

EDIT: I am using version 0.9.something of madwifi and 10.10 32-bit ubuntu.

Please help.

---

### Post by PatchesTheCaveman on 2010-12-31
Go to Applications > Accessories > Terminal and type the following and press Enter:
```
dmesg | grep -i madwifi
```

That will reveal the kernel errors you were talking about.  Copy and paste what outputs to a reply to this thread and we'll try and figure out what's causing them.

---

### Post by Papug9 on 2011-01-03
Kernel: 2.6.35-24 (generic)
I also seem to get some messages to do with atk5k as root on tty. (in text - no xorg)
I also upgraded madwifi to 0.10.5.3 (i think).

---


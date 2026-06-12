---
title: "Wi-Fi not working"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by raunhar on 2013-07-13
Ubuntu Version: 12.10 (64 Bit)
Laptop: Dell Inspiron
Ubuntu Version : 12.10 64 bit
The wi-fi not working. The wifi widget on the top does not show any available netork. Even , it does not connect to manually created wifi netork.

---

### Post by kc1di on 2013-07-13
Hello,

You most likely have a broadcom wireless card in that box.  and you will need to install the drivers for it first.
If you can get an Ethernet connection go to Software Center >edit>software sources>and additional drivers click on that see if it offers you
any drivers for your wiresless card and install it Or activate it and reboot you should have wireless after that.  
If that does not work.
go to a terminal and type the following command and post the output here.
```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

---

### Post by wildmanne39 on 2013-07-13
*Thread moved to **Networking & Wireless**.*

---


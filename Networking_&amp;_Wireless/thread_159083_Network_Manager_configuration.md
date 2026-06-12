---
title: "Network Manager configuration?"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by scb147 on 2006-04-12
I am experiencing problems using Network Manager with my new router, for details: [http://www.ubuntuforums.org/showthread.php?t=158021](http://www.ubuntuforums.org/showthread.php?t=158021)

I am wondering if Network Manager has any sort of configuration that I can change to attempt to get my Ubuntu notebook to connect up to my new router.  Network Manager just keeps trying to renew the IP, but it never actually acquires it.

I have Network Manager 0.4.1 installed.  Any help is greatly apprciated!

---

### Post by ErikTheRed on 2006-04-12
Can you give some specifics on your network? I've gotten network-manager to work to some extent. I have been able to connect to WEP and WPA Personal networks with no problem. I've failed at all attempts to connect to any WPA Enterprise network. I might be able to give you a hand, because it sounds like you are using a router, which probably is using WEP or WPA Personal.

BTW, I'm using KDE, so I'm using KNetworkManager, which I don't think is much different from plain old networkmanager.

EDIT: Sorry I didn't see at first that you were using wired. NetworkManager is still a testing product. I suggest you just submit a bug report. That's all you can do for right now.

---


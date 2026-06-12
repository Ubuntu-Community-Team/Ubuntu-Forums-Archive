---
title: "wireless 9.10 connection issue"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by anna3k1 on 2009-12-26
Hello! I am using ubuntu 9.10 on a 3 year old toshiba satellite. Everything was working fine until recently. My wireless card will no longer connect to the network. I have an intel PRO/set 3945abg internal card. It is enabled, it appears to be recognized, it can pick up on different wireless networks, but for some reason it doesn't want to connect.  I checked the WEP key, I tried booting into an older kernel, the routher is working just fine seeing as how I'm on it in my windows partition (dual-boot), I checked the settings on my router, and I even tried a different WEP key. When I try to connect to my network, the icon starts spinning as thought it's trying to talk to the router but it never connects. Sometimes when I reboot it gets on no problem but as soon as I try to use the connection it goes down. Might this be a virus or malware issue or possibly an update issue? any advice or help would be greatly appreciated. Also, note I am a beginner with linux so the easier, the better, lol.

---

### Post by lrcaballero on 2009-12-26
Are you dual-booting with Windows? if you are, there is a windows up-date that is causing this problem, does it also say limited connection or unidentify connection??? I am assuming you are dual-booting with windows: so the update you need to unistall is KB974455, also disable your IPv6 in your local connection menu.

Let me know how this goes!

Luis

---

### Post by anna3k1 on 2009-12-27
actually, I fixed it. I right clicked on the wireless icon, went to the edit connections page, then to wireless, then deleted the connection to my router. I then rebooted and let it find the network, entered in the key and it got on no problem. Thank you for the help! ^.^

---


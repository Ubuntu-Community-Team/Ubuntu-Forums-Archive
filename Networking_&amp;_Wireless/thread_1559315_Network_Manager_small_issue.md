---
title: "Network Manager small issue"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by nellock4 on 2010-08-23
I can connect to my wireless router but having a small annoyce doing so. My network manager is showing that I'm not connected and it can't find any wirless network. I have to uncheck the "networking" line then check it again. Then it connects to my router.
 
Only happens each time I turn on the computer so no big deal but it would be nice just to turn on the computer and have it connect without me having to make a few clicks. Any work around this or will I be doing this until an update comes out?
 
Thanks so much.

---

### Post by dineshs on 2010-08-23
[COLOR="DarkRed"]Connect automatically[/COLOR] is checked?
(right  click NM click edit connections-wireless-select the wireless device-edit)

---

### Post by nellock4 on 2010-08-23
Thanks for the response. I should have mentioned that it is already checked. Everything should just work but it doesn't. Anything else I can try?

---

### Post by dineshs on 2010-08-23
Can you post the contents of
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
mine says```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

```

---

### Post by nellock4 on 2010-08-31
Thanks. Sorry it took so long. Got it solved with your advice.

---


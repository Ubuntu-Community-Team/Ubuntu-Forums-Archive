---
title: "Administrative Alerts"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by CyberAxe on 2009-07-07
I'm running ubuntu server 9.04 i'd like to be able to send adminastrative alerts to all computers on the network (such as when the server is rebooting and such)

most of the computers are running xp home and there are also several macs running MACOS 10.3.9

i've tried searching the forums, looking at the documentation and googling but to no avail so any help would be appreciated

thanks

---

### Post by Iowan on 2009-07-07
Check **man wall**. Some commands (shutdown?) will notify users, but I'm not sure by what method.

---

### Post by CyberAxe on 2009-07-08
thanks, i've had a look at that command, but it seems to be linux only? or am i wrong? i did some googling but it only seemed to bring up linux stuff, there was not much info in man wall

i've also tried smbclient to no avail but that relies on having messenger enabled which i'd rather not do and doesnt seem to work for macs

---

### Post by Boondoklife on 2009-07-08
> **CyberAxe said:**
> thanks, i've had a look at that command, but it seems to be linux only? or am i wrong? i did some googling but it only seemed to bring up linux stuff, there was not much info in man wall

i've also tried smbclient to no avail but that relies on having messenger enabled which i'd rather not do and doesnt seem to work for macs

Yea and I think it is local only, you may want to just use the path of least resistance and just get a local chat server up and broadcast your own messages. I know winpopup used to be an option but vista took that out too.

---


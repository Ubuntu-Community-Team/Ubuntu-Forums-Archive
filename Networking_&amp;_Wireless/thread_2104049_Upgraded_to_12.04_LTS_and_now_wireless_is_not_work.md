---
title: "Upgraded to 12.04 LTS and now wireless is not working"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by newuser25 on 2013-01-11
Hello,

I recently updated to 12.04 LTS but now the wireless connections are not working. This is what's happening:

On booting, it says "waiting for network configuration," then "waiting an additional 60 seconds for network configuration"

When it first booted, no network connection icon would appear at all. I have since plugged in an ethernet cable, and since then the wireless connection appears and says it is connected, but the internet still does not work. Internet does work on the hardwired connection, and wireless is still working fine for all other computers in the house.

I have tried rebooting & power-cycling the modem and router, as well as the following fixes suggested on other forums:
[http://ubuntuforums.org/showthread.php?t=2001421](http://ubuntuforums.org/showthread.php?t=2001421)
as well as 
sudo apt-get update
sudo apt-get upgrade

I'm very keen to get my internet working properly again as it's been a week already. If the simplest way would be to go back to the old version, I'd also be happy to do that. Any advice much appreciated!

Thank you!
Graham

---

### Post by praseodym on 2013-01-12
Open the following file:

```
gksu gedit /etc/network/interfaces
```
remove anything _except_:
```

auto lo
iface lo inet loopback
```
Save, close the editor, and reboot.

---

### Post by newuser25 on 2013-01-14
Thank you so much! That worked!!! :)

---


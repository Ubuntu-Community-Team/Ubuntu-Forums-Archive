---
title: "Sky Netgear Router Keeps Rebooting"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by iiyama1 on 2009-04-28
I have put on Ubuntu 9.04 Netbook Remix (previously had Mint) everything is great except the following.
When my wireless network is detected I enter all the info as required, however, when I try to connect the router itself starts to reboot and does this several times. It will eventually connect after a while but it's doing my head in. I have also tried it on another persons sky router and it does the same?
I dual boot with XP (powerdvd) and this is fine. Im a bit lost on this so any help would be appreciated.
By the way Im newish to linux so im no power user :P

---

### Post by iiyama1 on 2009-04-28
Anybody?

---

### Post by inobe on 2009-04-28
so your "router" isn't rebooting meaning turning off and on, power off, power on ?

your connection simply drops ?

---

### Post by iiyama1 on 2009-04-28
No, its the physical router itself. When I hit connect the wireless symbol on the router starts to flash (as expected) then all the lights go out and come back as if it has rebooted. It will do this for as long as I am trying to connect. Eventually, it will stop rebooting and connect but I dont understand what it is causing the router to reboot itself when it is fine in XP.

---

### Post by inobe on 2009-04-28
delete the wireless connection and restart, upon restarting wait for the "network detected" prompt' then re-enter your credentials.

---

### Post by iiyama1 on 2009-04-28
I have sorted this out now, very odd. If I enable the display ssid option in the router config it works fine, disable this and I get the router reboot issue. Very strange
Thanks for your help

---

### Post by inobe on 2009-04-28
i figured there where multiple instances that caused the inconsistency, meaning if you delete the connection by right clicking and hit edit connections then removing' this could alleviate multiple instances.

---


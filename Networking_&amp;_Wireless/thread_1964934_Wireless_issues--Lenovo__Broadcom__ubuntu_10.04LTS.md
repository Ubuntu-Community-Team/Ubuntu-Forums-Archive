---
title: "Wireless issues--Lenovo / Broadcom / ubuntu 10.04LTS"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by pixellany on 2012-04-24
Hello!!

I am having an issue where the wireless connection periodically gets lost---eg after the computer comes out of suspend/sleep.  The typical pattern is that it reconnects, but cannot get an IP from the router.  It is normally (but not always) cured by re-booting.  The signal always shows strong in WICD

Re-starting the router typically does NOT help.

Lenovo Ideapad Z-560
Ubuntu 10.04 LTS--all updates current
Broadcom wireless
Netgear N300 router

thanks....

---

### Post by pixellany on 2012-04-26
Here's what I just got over at LinuxQuestions:
> I had same issue with my lenovo notebook. After suspend/sleep I could not get IP address. I found out that my wireless interface gets soft-blocked with rfkill. I solved it with script which pings the gateway periodically and if its down it unblocks the interface and restart the network:
Code:

```
rfkill unblock all
/etc/rc.d/rc.inet1 restart
```

On ubuntu these commands may differ.
Hope it helps.

---


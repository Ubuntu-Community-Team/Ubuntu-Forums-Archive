---
title: "wired internet works but only without router"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by tba967 on 2010-01-12
I am trying to use a Belkin F6D4230 "enhanced" wireless router to connect to the internet.  This setup works well for wireless but when I need to connect via ethernet cable, the setup doesn't work.  I am running 9.1 NBR on an eee pc 1005ha.  Oddly, it does work on the same netbook after booting into win7.  Also, my other laptop running ubuntu 9.1 works when it is plugged directly into the router.  As I indicated, ubuntu makes a wired connection successfully if I simply plug it directly into the cable modem.  I believe that the Eee PC 1005HA has an Atheros AR8132 ethernet adapter.   Does anyone have any idea what could be going on here?  I have already intalled the backports that are suggested on the NBR 9.1 compatibility page.

[FONT=Courier New]                       
wire->router      doesn't work, but works for other hardware and other OS          
wire->modem     works
wireless             works[/FONT]

---

### Post by shortcut144 on 2010-01-12
Could be that the wired interface is set for a static IP.  A lot of the home routers don't work well with that.  Most use DHCP.

Posting the output of 
```
cat /etc/network/interfaces
```

and ifconfig when the cable is plugged in and no plugged in could help.

I'm no expert but this where I would start.

---

### Post by tba967 on 2010-01-12
thank you for your suggestion. I actually just discovered that the problem has nothing to do with ubuntu.  it is purely something flukey with my router.

---


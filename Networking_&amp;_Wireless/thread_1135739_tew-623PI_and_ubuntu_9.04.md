---
title: "tew-623PI and ubuntu 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by kcihtred2 on 2009-04-24
ok when i installed i got a wireless thing up in the spot next to the clock.  however, when i go to connect to my network (wireless N, WPA encrypted), it wont connect.  Is it that it won't do WPA (personal btw) or what? anyone one else have this problem?

---

### Post by leww on 2009-07-06
I have the same card I had it working in 8.10, doesn't work in 9.04.  In the wonderful world of wireless Linux, everyone is a beta tester

---

### Post by leww on 2009-07-08
OK I took the TEW-623 card out and installed an edimax 7727in card, it didn't work either.

Then I took wpa2 off the router and went unencrypted.  That worked fine.

I then started to read the Jaunty bug reports.  It appears there is a known issue with jaunty and WPA/WPA2 connections  (they don't work).

---

### Post by leww on 2009-07-08
I finally solved my problem,  I took a WGA600N wireless gaming adapter, set it up with my wireless properties.  Then connected it to my ethernet port.

When I boot XP I use the EDIMAX card and when I boot Ubuntu I use the WGA600.


Really pretty sad, when I stop to think about it.

Ubuntu has a long way to go before it is anything but a hobby.

---


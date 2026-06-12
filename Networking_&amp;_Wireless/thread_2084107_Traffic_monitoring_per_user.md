---
title: "Traffic monitoring per user"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by PiVoKoZeL on 2012-11-14
Hi guys.
Is there a way how to monitor traffic (both down/up) per user? I want to know monthly traffic of every user.

Dist: Ubuntu desktop 12.04

---

### Post by gerowen on 2012-11-14
> **PiVoKoZeL said:**
> Hi guys.
Is there a way how to monitor traffic (both down/up) per user? I want to know monthly traffic of every user.

Dist: Ubuntu desktop 12.04

Are there multiple users on one computer, or does each user have their own computer that you want to monitor?

If everybody has their own computer, you could check out the firmware on your router.  I flashed mine with DD-WRT and it supports traffic monitoring.

To monitor network use from individual users, you could use any of a number of network monitoring tools available in the software center.  I believe etherape is a popular one.  You could script it to run in the background when they log in and have it save the log information to a text file you can go look at later.

---

### Post by PiVoKoZeL on 2012-11-14
I have Ubuntu desktop with multiple users. Everyone has Its own account. 
I tried some network utilities but every utility logs only total traffic or traffic per port. I tried cacti with plugins, ntop, vnstat but with no sucess.

---


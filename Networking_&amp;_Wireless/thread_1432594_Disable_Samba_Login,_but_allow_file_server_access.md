---
title: "Disable Samba Login, but allow file server access?"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-03-17
When using security = user with Samba, you have to have a unix account on the system for that user. Okay, fine. But then that user comes up as a user who can log into this system.

Is there a way to disable that user's access to logging on to the computer (at least take it off the main screen so it's not displayed) while still allowing the user to have file server access?

---

### Post by jrssystemsnet on 2010-03-18
> **Roasted said:**
> When using security = user with Samba, you have to have a unix account on the system for that user. Okay, fine. But then that user comes up as a user who can log into this system.

Is there a way to disable that user's access to logging on to the computer (at least take it off the main screen so it's not displayed) while still allowing the user to have file server access?Typically what I do is set the shell for the user to /usr/sbin/nologin.  To be honest I'm not sure whether that takes the user off gdm's graphical list of users or not, but it certainly ought to - and they won't be able to actually log in either way.

---


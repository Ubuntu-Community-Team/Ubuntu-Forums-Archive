---
title: "Different users with different display settings?"
date: 2011-07-31
forum: Multimedia Software
---

### Post by szivak009 on 2011-07-31
Hi dear forum members!

I'd like to do something, but I don't seem to find the solution. Here is my problem: I have a laptop and I plugged in another monitor to it. What I want to do is when UserA logs in, both of the monitor is used, but when UserB logs in, only one of the monitor is used. When I change the display settings it applies to the other user too. I'd like to have different display settings for each user.

How can I do this?

Thank you very much.

szivak009

---

### Post by szivak009 on 2011-07-31
Forgot to mention that I have an Ati HD 4570 video card, and using ATI Catalyst Control Center.

---

### Post by realzippy on 2011-07-31
...maybe "[disper]("http://willem.engen.nl/projects/disper/")" can help.No need for creating another user.

---

### Post by szivak009 on 2011-07-31
No no... my purpose is to DO have different settings with two users.

Thanks for the tip, by the way.

---

### Post by realzippy on 2011-07-31
So you should try to do your settings with *xrandr* or "Monitors" GUI,
not with catalyst control center.

---

### Post by szivak009 on 2011-08-03
Thanks for the tips! I will try them.

---

### Post by aeiah on 2011-08-03
if you can control your monitors with xrandr, you can put the commands into a script that executes when each user logs in

---

### Post by realzippy on 2011-08-03
> **aeiah said:**
> if you can control your monitors with xrandr, you can put the commands into a script that executes when each user logs in

eg:
/etc/gdm/Init/Default

---


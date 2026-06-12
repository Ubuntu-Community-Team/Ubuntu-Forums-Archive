---
title: "Nautilus_2.32.2.1-0ubuntu4 crashes"
date: 2011-01-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-13
Has anyone here experienced this same nautilus crash with the most recent version 2.32.2.1-0ubuntu4?
It is easily reproduced. In my system Nautilus crashes when I move mouse cursor on it, every time.
Downgrading to the version 2.32.2.1-0ubuntu3 resolves the issue.

---

### Post by mc4man on 2011-01-13
nautilus is fine here (2 installs - 1 is 2 wk. old + updates, the other 2 day old +, different hardware
But then again these 2 installs are behaving slightly differently, can't find much consistency as of yet in natty

---

### Post by Harry33 on 2011-01-13
I have 64-bit architecture and I am seeing these crashes with gnome-classic.

---

### Post by mc4man on 2011-01-13
The patch definitely seems suspect. (margin

While it doesn't cause an issue here on a Classic - panel login (32 bit) as far as nautilus -  when returning to a Desktop unity login it will only work once
Then it crashes Unity on subsequent Desktop logins

On a machine that is only a unity login after the update unity crashes

So it wouldn't be surprising if it created mis behavior as you've seen

Edit: a fresh install with latest .iso, then fully updated resolved any issue as seen in Desktop > unity

---

### Post by Harry33 on 2011-01-14
Here is the bug report about this issue:
Bug #702858
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/702858](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/702858)

---

### Post by Harry33 on 2011-01-15
I have done more investigating.
Actually Nautilus crashes if I have set the panel to autohide and then I unhide it with mouse.
I'm using Gnome-classic and I have made an additional sidepanel, which is set to autohide.
Now if I remove the autohide setting, the issue is gone.

Could you test this with your systems, just add a panel with an autohide option on.

---

### Post by Harry33 on 2011-01-16
This bug has been fixed with the update of Nautilus_2.32.2.1-0ubuntu5.

---


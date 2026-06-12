---
title: "Classic Desktop- Missing icon images in Panel"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rockyrobin on 2011-04-12
I installed Natty yesterday as an upgrade from Maverick and everything seems good barring a problem with 'Notification' panel applet icons not showing up when using 'Classic Desktop'. In their place there appears to be a placeholder image icon with a red circle with a red line through it. This can also be seen on the login screen as the 'Accessabillity' icon there is the same. Is anyone else experiencing this after a 'update-manager -d' upgrade recently?

---

### Post by Harry33 on 2011-04-12
> **rockyrobin said:**
> I installed Natty yesterday as an upgrade from Maverick and everything seems good barring a problem with 'Notification' panel applet icons not showing up when using 'Classic Desktop'. In their place there appears to be a placeholder image icon with a red circle with a red line through it. This can also be seen on the login screen as the 'Accessabillity' icon there is the same. Is anyone else experiencing this after a 'update-manager -d' upgrade recently?

That is a known persisting bug in libappindicator and notification area in the panel.
It has also been discussed here on the forum recently.

Here is the bug report (741385):
[https://bugs.launchpad.net/ubuntu/+s...or/+bug/741385](https://bugs.launchpad.net/ubuntu/+s...or/+bug/741385)

There was another bug in ubuntu-mono related to this, which is fixed now, but the broken notification area did not got fixed.

Anyway, there is a good workaround for this:
downgrade the package libappindicator1 (0.3.0-0ubuntu1)
to the previous version (0.2.99-0ubuntu1),
then reboot.

You can find the working libappindicator1 here (select the architecture first, 32-bit or 64-bit):
[https://launchpad.net/ubuntu/+source....2.99-0ubuntu1](https://launchpad.net/ubuntu/+source....2.99-0ubuntu1)

---


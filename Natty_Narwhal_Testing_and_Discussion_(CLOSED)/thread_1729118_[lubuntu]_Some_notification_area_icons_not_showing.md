---
title: "[lubuntu] Some notification area icons not showing up"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dearingj on 2011-04-14
Anyone else have this problem?
I'm running Lubuntu Natty. Some programs' icons in the notification area are only showing up as this generic icon.

In the attached screenshot, the nonfunctioning icons are (from left to right):
Network Manager (GNOME's nm-applet I think)
Battery monitor
Tomboy Notes
Banshee

I do like Banshee and Tomboy, but could replace the other two if necessary.

---

### Post by Harry33 on 2011-04-14
> **dearingj said:**
> Anyone else have this problem?
I'm running Lubuntu Natty. Some programs' icons in the notification area are only showing up as this generic icon.
In the attached screenshot, the nonfunctioning icons are (from left to right):
Network Manager (GNOME's nm-applet I think)
Battery monitor
Tomboy Notes
Banshee
I do like Banshee and Tomboy, but could replace the other two if necessary.

Might be this bug (741385):
[https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/741385](https://bugs.launchpad.net/ubuntu/+source/libappindicator/+bug/741385)

Try downgrading libappindicator1_0.3.0-0ubuntu1
to the previous one
libappindicator1_0.2.99-0ubuntu1

---

### Post by dearingj on 2011-04-14
That did it, alright! Thanks.

---

### Post by Harry33 on 2011-04-15
> **dearingj said:**
> That did it, alright! Thanks.

You may now upgrade back to the libappindicator1_0.3.0-0ubuntu1 version.
This bug has been fixed with the new GTK+2 update (version gtk+2.0 2.24.4-0ubuntu2).

There is another bug report (746495) about notification area icons here:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/746495](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/746495)

This is now fixed and fix released.

---


---
title: "Update Dialog Popping Up"
date: 2012-06-10
forum: Mythbuntu
---

### Post by uncle hammy on 2012-06-10
On one of my frontends (12.04), despite the having "notification icon in panel" selected under update manager behavior in the Mythbuntu Control Center, every time there are updates, the entire update dialog pops up over top of everything else.

Anyone have any idea how to make this annoying giant go away?

Thanks

---

### Post by Enigmapond on 2012-06-10
Yea you can do what I did in 9.04 when I was encountering the same problem....purge the update manager. I never use the silly thing anyway and always update from the terminal.

---

### Post by uncle hammy on 2012-06-12
Thanks, but that's a band-aid, not a solution.

---

### Post by ernstp on 2012-06-13
I also have that and un-checking the box in mythbuntu control center and running
gconftool -s --type bool /apps/update-notifier/auto_launch false
doesn't help!

---

### Post by tgm4883 on 2012-06-13
Is this on a Mythbuntu or Ubuntu install?

---

### Post by ernstp on 2012-06-13
> **tgm4883 said:**
> Is this on a Mythbuntu or Ubuntu install?

Mythbuntu with xfce

---

### Post by uncle hammy on 2012-06-14
Ditto, Mythbuntu 12.04

---

### Post by Boppy3125 on 2012-06-14
One of my frontends was upgraded from 11.10 to 12.04.  When it was 11.10 it worked correctly where it put the little notification icon up there and that's it.  12.04, both machines running Mythbuntu (one was this upgrade, the other was fresh build of 12.10) doing this popup that gets in the way.  This is affecting WAF.

---


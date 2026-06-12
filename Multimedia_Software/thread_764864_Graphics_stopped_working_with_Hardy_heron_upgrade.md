---
title: "Graphics stopped working with Hardy heron upgrade"
date: 2008-04-24
forum: Multimedia Software
---

### Post by jackread on 2008-04-24
I'm wondering if anyone knows what's going on with the intel 965 chips, right now.I was running ubuntu 8.04 RC fine, yesterday, and when I upgraded today and rebooted... my computer will only run in low graphics mode. 

Has the intel chip been blacklisted?

---

### Post by jackread on 2008-04-25
I fixed this and got out of "low graphics mode" by going to etc\X11\xorg.conf and replacing with the back up (that ubuntu makes everytime settings are changed ((it was called xorg.conf.1)) ). BOOM. back to normal.

---


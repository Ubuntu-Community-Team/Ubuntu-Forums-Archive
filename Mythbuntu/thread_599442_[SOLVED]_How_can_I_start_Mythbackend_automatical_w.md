---
title: "[SOLVED] How can I start Mythbackend automatical when I start Mythbuntu?"
date: 2007-11-01
forum: Mythbuntu
---

### Post by Archmage on 2007-11-01
I did install Mythubuntu 7.10 and notice that Mythbackend isn't starting automatical at startup, although this machine should be a front+backend-combination. Therefore starting a front only is a little bit stupid.

Is there any way to let the backend start automatical when starting the system?

---

### Post by superm1 on 2007-11-01
> **Archmage said:**
> I did install Mythubuntu 7.10 and notice that Mythbackend isn't starting automatical at startup, although this machine should be a front+backend-combination. Therefore starting a front only is a little bit stupid.

Is there any way to let the backend start automatical when starting the system?
checkout /var/log/mythtv/mythbackend.log

most common cause is wrong permissions on your recordings directory.

---

### Post by Archmage on 2007-11-05
Thank you. That was exactly the information that I need to find my mistake. Mythbackend is now starting.

---


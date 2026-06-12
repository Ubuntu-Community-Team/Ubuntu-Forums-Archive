---
title: "Frontend black after upgrade to 9.04."
date: 2009-04-24
forum: Mythbuntu
---

### Post by Archmage on 2009-04-24
After upgrading from 8.10 to 9.04 the Mythtvfrontend had gone black.

If you start it, I see black with a black square on it (you notice because of the light colored edges) and after a while it turns total black. I think at this point the caching is over. I mange to start a video blind and if I hit escape often enough I see a long square, if I go down I can quite the frontend, but that is all.

I did remove every theme beside Mythcenter, but I'm still seeing nothing. :(

---

### Post by minirx7 on 2009-04-25
> **Archmage said:**
> After upgrading from 8.10 to 9.04 the Mythtvfrontend had gone black.

If you start it, I see black with a black square on it (you notice because of the light colored edges) and after a while it turns total black. I think at this point the caching is over. I mange to start a video blind and if I hit escape often enough I see a long square, if I go down I can quite the frontend, but that is all.

I did remove every theme beside Mythcenter, but I'm still seeing nothing. :(

Do you have an ATI card?  I dont know i have the same issue, but there is a bug report out.

---

### Post by Archmage on 2009-04-25
Yes, ATI Radeon XPRESS 200 5974 (PCIE).

Do you have the link to the bugreport? I can't assume that you already know when this will be fixed? ;)

---

### Post by superm1 on 2009-04-25
Here's the bug:

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898)

It's ATI specific (and mentioned in the release notes for 9.04)

There is a workaround in that thread to launch with an environment variable or to disable DRI

---


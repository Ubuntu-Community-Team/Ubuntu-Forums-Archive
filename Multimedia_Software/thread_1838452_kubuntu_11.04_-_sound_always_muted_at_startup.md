---
title: "kubuntu 11.04 - sound always muted at startup"
date: 2011-09-03
forum: Multimedia Software
---

### Post by purct on 2011-09-03
i recently re-installed my laptop with Kubuntu 11.04 and have been having problems with the volume setting not being saved/restored at startup.   The volume is alway at 0% at startup.

After a few days of looking for a solution, I finely worked out how to resolve it.

In the mixer, select settings menu and configure kmix

under "behaviour" options, remove the tick from "Restore volumes on login"

it appears to be reverse - i.e. when its ticked the settings aren't restored!

---

### Post by Wild_Duck66 on 2012-01-04
Thanks, I`ve had this problem only on my Laptop for years and no change with every upgrade. Now I have sound without having to unmute. On my Desktop (also Kunbuntu) I have to do a "xset -dpms s noblank" command or I get a blank screen after 5 minutes.
Thanks again.

---


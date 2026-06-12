---
title: "How do I tell what graphics driver I'm using?"
date: 2009-05-20
forum: Multimedia Software
---

### Post by MadCatmkII on 2009-05-20
Hi

I'm still trying to figure out what graphics driver I'm using. I have a Ati x1950x, one of the recently legacized (spelling?) cards, so I know it isn't the proprietary one. So how can I tell what driver I'm using?

---

### Post by lukeiamyourfather on 2009-05-20
There's an icon in the Administration menu called Hardware Drivers and it should show if any proprietary drivers are in use. Cheers!

---

### Post by mcduck on 2009-05-20
```
lsmod | grep drm
``` works fine. ;)

Most likely you are using the "radeon" driver, which is the default for Ati cards.

---

### Post by MadCatmkII on 2009-05-20
Yep, lsmod says I'm on the radeon driver. That means the best driver for my circumstances, right? (remembering that I have an older card where proprietary drivers won't work)

---

### Post by mcduck on 2009-05-21
> **MadCatmkII said:**
> Yep, lsmod says I'm on the radeon driver. That means the best driver for my circumstances, right? (remembering that I have an older card where proprietary drivers won't work)

Yes, it should be the best one.

Actually I've found the "radeon" driver to be even better than Ati's own drivers in many things.. Ati's proprietary driver gave a bit better 3D performance, but had a lot problems with video, suspending, dual screens etc.. With the open-source radeon driver all those problems are gone and 3D performance is just fine for my needs.

---

### Post by MadCatmkII on 2009-05-22
Thanks for your help. Now I can go and try to figure out how to tweak this thing!

---

### Post by markbuntu on 2009-05-22
Look in the /var/log/Xorg.0.log and you can see how the options have been set for the driver by default before you go tweaking them around.

---


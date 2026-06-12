---
title: "nvidia component out HD playback in 8.04 broken -- fix included here"
date: 2008-07-27
forum: Mythbuntu
---

### Post by majoridiot on 2008-07-27
in doing a rebuild of my main server and upgrading with a fresh install to 8.04,
i discovered that the component out for 720p with the nvidia proprietary driver is
broken- HD or SD video exhibit terrible tearing.  
after a bit of examination, i  that xorg.conf- as configured by mythbuntu
on install- is missing a critical section.

if you are fighting tearing issues on your nvidia installation, check /etc/X11/xorg.conf
for the following- if it is missing, add it:

```
Section "Extensions"
    Option "Composite" "Disabled"
EndSection
```

adding this section fixed all tearing problems.

(although i'm not using xvmc, you'll probably need it for that, too.)

---

### Post by yonkiman on 2008-09-24
Yes!  Thank you!  I've been trying to get rid of the tearing for a while, not sure why I'm just now seeing the post, but that's it!

BTW, how did you figure it out?  That solution seems a little obscure...

Thanks again!

(Keywords: tearing, vsync.)

---

### Post by majoridiot on 2008-09-24
> **yonkiman said:**
> Yes!  Thank you!  I've been trying to get rid of the tearing for a while, not sure why I'm just now seeing the post, but that's it!

BTW, how did you figure it out?  That solution seems a little obscure...

Thanks again!

(Keywords: tearing, vsync.)

glad this helped you!

some idiots thrive on/in obscurity... ;)

---


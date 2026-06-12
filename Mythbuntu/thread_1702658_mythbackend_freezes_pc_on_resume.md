---
title: "mythbackend freezes pc on resume"
date: 2011-03-08
forum: Mythbuntu
---

### Post by veehexx on 2011-03-08
i'm having issues when my mythtv box resumes from suspend.

i'm running FE and BE on the same machine, and initiating the sleep via irexec & a script using pm-suspend.

so far i've traced it to the BE causing the issue; if i 'killall' the BE before entering suspend, then the pc resumes fine, untill BE is started again.
i dont know if it's related, but it froze when i attempted to watch live tv.

i cant find any definative fixes on google, some sugest unloading certain modules (which ones? - the blogs werent that accurate), and others say closing down certain programs (one said mysql, mythbackend and mythfrontend).
i'm very confused at exactly how to find out whats causing the crash and how to go about possible fixes.

any help appreciated

---


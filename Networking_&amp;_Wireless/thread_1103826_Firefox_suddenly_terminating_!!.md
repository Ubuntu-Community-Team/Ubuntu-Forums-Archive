---
title: "Firefox suddenly terminating !!"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by ddastoor on 2009-03-23
Hi All, 
Firefox suddenly termates without a crash notification or anything. This happens during casual browsing. Is it a Desktop environment problem, a Firefox problem, etc?

System: Dell Inspiron 6400 Laptop
Ubuntu 8.10 Intrepid Ibex (regular gnome)
Later, did a "apt-get install kubuntu-desktop"

Any ideas?

Thanks.

---

### Post by kaibob on 2009-03-23
> **ddastoor said:**
> Hi All, 
Firefox suddenly termates without a crash notification or anything.... Any ideas?

Many Firefox issues are resolved by creating a new profile. To do this, enter "firefox -ProfileManager" in a terminal window.

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

If Firefox runs properly with the new profile, you can copy over your bookmark and any other user files and, after a test period, delete the old profile. 

Firefox extensions and plugins (especially Flash) are a frequent problem. As an alternative to a new profile, you may want to disable extensions/plugins to see if that helps.

---

### Post by ddastoor on 2009-03-23
Thanks kaibob, that helped. However, when if I reinstall, say the adobe flasg plugin, will I have the same problems again?

THanks.

---

### Post by kaibob on 2009-03-23
> **ddastoor said:**
> Thanks kaibob, that helped. However, when if I reinstall, say the adobe flasg plugin, will I have the same problems again?

THanks.

I don't know but one reason for doing things this way is to isolate exactly what extension or plugin is causing the problem. So, I would install flash (but no other extension/plugin) and then run Firefox to see if you have any issues. If flash is the problem, there are some alternatives that you can try (i.e. older or newer versions of flash and if I remember correctly, there is an open-source version).

---


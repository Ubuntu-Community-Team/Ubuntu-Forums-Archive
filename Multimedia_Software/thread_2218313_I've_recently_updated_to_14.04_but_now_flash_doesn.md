---
title: "I've recently updated to 14.04 but now flash doesn't work..."
date: 2014-04-20
forum: Multimedia Software
---

### Post by uzk20707 on 2014-04-20
During the update of 14.04, I noticed something odd in that it said it had 'disabled third party drivers' (which I made a mental note of to correct because several systems relied on them). After installing, it failed to correctly implement my previous keyboard settings (GB switched to US: it never asked my preferences) and I found that flash player doesn't work.

Using terminal to install doesn't work because it says the flash driver is up to date. So either the third party drivers are still disabled and need re-enabling, or I need to do that trick where you drag the flash file into the correct folder (which despite my best efforts to discover again, can't because I keep picking up ubuntu searches with suggestions that only work in ubuntu).

So, how do I re-enable third party drivers in Lubuntu?

---

### Post by mörgæs on 2014-04-20
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---


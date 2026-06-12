---
title: "Does anyone have diskless suspend working?"
date: 2009-02-26
forum: Mythbuntu
---

### Post by rlowery on 2009-02-26
Hi Folks,

I've recently started playing around with a diskless mythbuntu frontend setup using jaunty after spending a couple of years rolling my own diskless images based on ubuntu-mythtv-frontend running on a standard ubuntu release.

For some reason whenever I try to suspend on a mythbuntu generated diskless image (via echo mem > /sys/power/state), the frontend completely locks up, with the mythtv menu still visible, but completely locked up.  Suspend works fine on my own diskless images based on intrepid.

Before I log a bug with the kernel team can anyone confirm if
a) This is a known general jaunty bug
b) This is a bug specific to jaunty diskless images
c) This is a limitation with mythbuntu generated diskless images in general (eg is intrepid also affected?)

If suspend is working fine for you in jaunty, please let me know and I'll try to investigate further on my setup (AOpen MP965-DR minipc).

Troubleshooting tips appreciated.

Cheers

-Rob

---


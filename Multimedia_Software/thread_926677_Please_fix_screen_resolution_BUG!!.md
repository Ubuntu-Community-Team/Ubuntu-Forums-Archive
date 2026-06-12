---
title: "Please fix screen resolution BUG!!"
date: 2008-09-22
forum: Multimedia Software
---

### Post by davidw89 on 2008-09-22
Nvidia  7300GT ---> Hardware Driver ---> It downloads an old version of Nvidia Driver from the repository --> reboot ---> low screen resolution (800x600) and you cannot change it.

It has happened very often!! But only on older graphic cards.

Fix is Downlaod EnvyNG then it will install a MUCH MORE NEWER version of nvidia Driver and that works. But it isn't "enabled" in Hardware Driver. But now i stuffed it up again buy installing it from the repository...

What's the problem here? Is this common?

---

### Post by aeiah on 2008-09-22
its not a bug per se, its more a lack of feature in the old stable drivers i think. im suprised you cant do it from the nvidia control panel with that card though. my 7800gt works fine. have you installed the nvidia-tools package? its a better control panel than the limited gnome 'change resolution' dialog box.

you can probably edit your xorg.conf too if you fancy it. back it up though. ive managed to get my graphics card to do most things with the standard nvidia drivers without needing to go bleeding edge including hdtv resolution-within-a-resolution stuff to eliminate overscanning etc.

---


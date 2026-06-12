---
title: "Mythbuntu control center and auto login"
date: 2007-10-27
forum: Mythbuntu
---

### Post by mrkite00 on 2007-10-27
I think I may have found a bug:

Open Mythbuntu control center, go to Artwork and login, disable automatic login, hit apply. I always get that message: "no change detected".

And of course, automatic login is not disabled.

Thanks

---

### Post by superm1 on 2007-10-27
Yeah this was an unfortunate bug that cropped up due to fixing one where it was always turned on.

[https://bugs.edge.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/156475](https://bugs.edge.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/156475)

For now, just edit /etc/gdm/gdm-cdd.conf

Change the two lines near the top from AutomaticLoginEnable=true to AutomaticLoginEnable=false

and TimedLoginEnable=true to TimedLoginEnable=false

---


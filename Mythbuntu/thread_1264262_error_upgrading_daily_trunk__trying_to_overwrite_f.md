---
title: "error upgrading daily trunk:  trying to overwrite file in other package"
date: 2009-09-12
forum: Mythbuntu
---

### Post by sfp-a7x on 2009-09-12
When upgrading to 0.22.0~trunk21783-0ubuntu0~mythbuntu1 (daily trunk PPA) on Jaunty, I get the following error:

```
E: /var/cache/apt/archives/mythtv-common_0.22.0~trunk21783-0ubuntu0~mythbuntu1_all.deb: trying to overwrite `/usr/share/mythtv/themes/MythCenter-wide/title/title_dvd.png', which is also in package mythtv-theme-mythcenter-wide
```

When I try to uninstall mythtv-theme-mythcenter-wide, apt first tries to fix some mythtv packages that were broken by the failed mythtv-common upgrade.  It does this by attempting to upgrade mythtv-common.  This of course fails since mythtv-theme-mythcenter-wide is still installed.  Chicken and egg problem.  Anyone know how to resolve this?

Thanks!

---

### Post by sfp-a7x on 2009-09-12
Never mind:  [https://bugs.launchpad.net/bugs/428211](https://bugs.launchpad.net/bugs/428211)

---


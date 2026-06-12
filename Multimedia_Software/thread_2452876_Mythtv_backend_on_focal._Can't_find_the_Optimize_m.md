---
title: "Mythtv backend on focal. Can't find the Optimize_mythdb.pl script?"
date: 2020-10-29
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2020-10-29
I moved my stuff into Docker recently. I was trying to make my crontabs internal to my containers so I just build and let em run. However that script doesn't seem to exist on Focal's version. There isn't much information. The mythtv page suggests creating a find orphans .py file but it doesn't say (that I can find) whether this replaces the old optimize script or what. Anyone what the right course of action is?

---

### Post by Tadaen_Sylvermane on 2020-11-20
Marking solved. After much sorting I found I was missing 2 packages. libdbi-perl & libmythtv-perl. I cannot explain why they didn't come down automatically on the install. I also had to manually create the actual optimize_mythdb.pl script. Copied from their git and added it to from my Dockerfile.

---


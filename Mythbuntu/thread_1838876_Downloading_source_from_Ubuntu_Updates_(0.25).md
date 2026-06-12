---
title: "Downloading source from Ubuntu Updates (0.25)"
date: 2011-09-04
forum: Mythbuntu
---

### Post by avelach on 2011-09-04
Hi,

I have installed MythTV 0.25 from Ubuntu Updates. Now I want to install source code from the same repository. When I do:

sudo apt-get source mythtv

It tries to download 0.24-fixes source code which obviously is not what I want. Does someone know how to do it?

Regards

---

### Post by superm1 on 2011-09-05
This means you are missing a deb-src line for the 0.25 repository.  Examine all your sources in /etc/apt/sources.list and /etc/apt/sources.list.d/ and find the one that specifies the 0.25 repository.   Add another line that is identical but switch out the starting "deb" for "deb-src"

---

### Post by avelach on 2011-09-05
Thanks! I missed the /etc/apt/sources.list.d/mythbuntu-repos.list file which holds the 0.25 repository. Solved then!

Thanks a lot!

---


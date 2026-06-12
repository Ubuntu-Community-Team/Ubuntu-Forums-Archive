---
title: "If Rapid Photo Downloader crashes for you on Ubuntu 20.04 . . ."
date: 2020-04-23
forum: Multimedia Software
---

### Post by dlynch3 on 2020-04-23
If you install [Rapid Photo Downloader]("https://damonlynch.net/rapid/") from the Ubuntu 20.04 Universe repository, as at the time of writing this forum post the version that will be installed is 0.9.22. On some machines (I don't know how many), version 0.9.22 will segfault (crash) on startup. Hopefully that won't happen to you but if it does, version 0.9.23 fixes the problem. Unfortunately I was not able to release 0.9.23 in time for inclusion in Ubuntu 20.04 (I am the developer). There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/rapid-photo-downloader/+bug/1873944") to upgrade the Ubuntu 20.04 Universe package to 0.9.23, but for now it's not been assigned to anyone. 

If 0.9.22 does crash on startup on your machine, please file a bug report. They're always useful. Here are some [instructions]("https://damonlynch.net/rapid/help.html") on how to do that most effectively. 

If 0.9.23 does not make it into Universe for Ubuntu 20.04 in a timely manner, you can always install the latest version of Rapid Photo Downloader using the [installation script]("https://damonlynch.net/rapid/download.html") I supply. It's hardly ideal, but it's better than nothing. A snap package will hopefully be released in the next year or so. It's actually quite difficult to have it running confined. Snap itself needs to be updated for it to run properly.

In case you're wondering what an earth this program is, this is what it looks like:

---


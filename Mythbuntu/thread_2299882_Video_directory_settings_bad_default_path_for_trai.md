---
title: "Video directory settings: bad default path for trailers"
date: 2015-10-22
forum: Mythbuntu
---

### Post by Bob_Blockerlundt on 2015-10-22
Should default video directories settings all start with /var/lib/mythtv?

In MythTV Frontend > Setup > Video Settings > General Settings > first page showing directories, every path is in the format of /var/lib/mythtv/blah, where blah is videos, coverart, screenshots, banners, and fanart.  The only exception is for trailers, which has this path:

/home/test/.mythtv/MythVideo/Trailers

Is this a bug?  I don't even have this path on my system.  It should match the other paths and use /var/lib/mythtv/trailers.

Sorry if this is already a known issue or already fixed.  I tried searching that path on Google, and the only result I got was
[https://lists.launchpad.net/mythbuntu-dev/msg00016.html](https://lists.launchpad.net/mythbuntu-dev/msg00016.html)
which appears to be some sort of code merge notification from 2010.  But I did not see any forum posts or bug reports.

This is on a fresh install of Kubuntu 14.04.3 and I got the latest package of mythtv, both backend and frontend on a single box:
sudo apt-get install mythtv

Version shows:
apt-cache show mythtv
...
2:0.27.0+fixes.20140324.8ee257c-0ubuntu2

---


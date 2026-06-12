---
title: "Unable to run Kodi after upgrade to 16.04.1 + other minor issues"
date: 2016-08-01
forum: Mythbuntu
---

### Post by scottn2 on 2016-08-01
Did an in place upgrade of Mythbuntu today from 14.04 to 16.04.1. Mostly it went smoothly except for the following:

1. Mythweb didn't work off the bat - had to install the php-db package to make 
it work. Once I had figured out that it seems to be OK.
2. I didn't have the SQL tweaks enabled so I didn't run into the [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-common/+bug/1576767) bug.

The biggest issue I found was that I was that Kodi had been removed and was unable to be re-installed. I'm raising this here because I believe it is a MythTV issue and not a Kodi issue. The issue is Kodi requires libtag1v5 while MythTV requires libtag1c2a - yes I am using the 0.28 repository. Ubuntu 16.04 comes with libtag1v5 by default.

root@mythtv:~# apt install libtag1v5 libtag1v5-vanilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libmyth-0.28-0 libtag1-vanilla libtag1c2a mytharchive mythbrowser mythbuntu-bare-client
  mythbuntu-desktop mythgallery mythmusic mythnetvision mythnews mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-dbg mythtv-frontend
  mythtv-theme-mythbuntu mythtv-transcode-utils mythweather mythweb
The following NEW packages will be installed:
  libtag1v5 libtag1v5-vanilla
0 upgraded, 2 newly installed, 22 to remove and 0 not upgraded.
Need to get 284 kB of archives.
After this operation, 310 MB disk space will be freed.
Do you want to continue? [Y/n] 

Is there a known workaround for this?

Thanks

---

### Post by scottn2 on 2016-08-02
Raised as bug [https://bugs.launchpad.net/mythbuntu/+bug/1609169](https://bugs.launchpad.net/mythbuntu/+bug/1609169)

---

### Post by tgm4883 on 2016-08-03
> **scottn2 said:**
> Raised as bug [https://bugs.launchpad.net/mythbuntu/+bug/1609169](https://bugs.launchpad.net/mythbuntu/+bug/1609169)

I've replied to the bug report. MythTV uses libtag1v5. I'm not sure where you got libtag1c2a

---

### Post by scottn2 on 2016-08-03
OK. Fixed. Haven't been able to determine why but for some reason something was being held. I ended up taking the plunge and uninstalling mythv (apt remove) and then installed kodi and then mythtv and now everything is working again. The bug report has been updated as well with more details. Hope this helps anyone else with the same issue.

---


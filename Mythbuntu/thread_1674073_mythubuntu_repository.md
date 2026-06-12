---
title: "mythubuntu repository"
date: 2011-01-23
forum: Mythbuntu
---

### Post by tritron on 2011-01-23
I wonder if anyone know how to add latest repository of mythtv one compiled from git master. 
I was trying to add 0.25 repository but it did not work so I removed link to it from but now I get errors running apt-get update 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
W: Failed to fetch [http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
How I can fix it.

---

### Post by tgm4883 on 2011-01-23
> **tritron said:**
> I wonder if anyone know how to add latest repository of mythtv one compiled from git master. 
I was trying to add 0.25 repository but it did not work so I removed link to it from but now I get errors running apt-get update 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
W: Failed to fetch [http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mythbuntu/master/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
How I can fix it.

If you are still getting those errors then you didn't remove it. With that being said, the PPA that currently builds from trunk is called 0.25 (since it will become 0.25). It is currently build built for 10.04 and 11.04 only.

---


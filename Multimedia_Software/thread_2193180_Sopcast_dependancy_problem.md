---
title: "Sopcast dependancy problem"
date: 2013-12-11
forum: Multimedia Software
---

### Post by che47audio on 2013-12-11
I'm trying to install Sopcast on Ubuntu 13.10 and found the following link when searching on where i could get an installation from. I added the ppa successfully but upon install l came across the following error and I don't have any idea of how to solve it.


```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 sopcast-player : Depends: sp-auth (>= 3.0.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```


Anyone any ideas. i appreciate your time.

Thanks

---

### Post by ian-weisser on 2013-12-11
PPAs are not community-supported software. Use them at your own risk.

You should contact the PPA maintainer, and let them know that their software broke your package manager.

Until they resolve the issue, all I can suggest is that you disable the PPA and clear those PPA packages from your cache to get your package manager working again.
You will not receive security updates, nor any other updates, until you fix your package manager.

---


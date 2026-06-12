---
title: "problems installing nvtv"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by theolster on 2006-08-03
Hi I'm having a few problems installing nvtv...
> mythtv@ubuntu:~$ sudo apt-get install nvtv
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvtv: Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1.1 is to be installed
        Depends: libglib2.0-0 (>= 2.9.3) but 2.8.3-0ubuntu1 is to be installed
        Depends: libpango1.0-0 (>= 1.11.2) but 1.10.1-0ubuntu1 is to be installed
E: Broken packages
mythtv@ubuntu:~$
I presume that I am missing some repos from my sources.list file - Any ideas?

---


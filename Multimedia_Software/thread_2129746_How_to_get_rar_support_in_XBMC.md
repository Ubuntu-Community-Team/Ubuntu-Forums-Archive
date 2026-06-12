---
title: "How to get rar support in XBMC?"
date: 2013-03-27
forum: Multimedia Software
---

### Post by ogoun on 2013-03-27
Hi,

I just noticed that under Ubuntu XBMC can't see the movies packed in rar archives. The XBMC wiki says:

> Note that XBMC from the official Ubuntu repository does not include rar support. [Source]("http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux#Ubuntu_2")

I then added the official PPA ppa:team-xbmc/ppa and installed XBMC 12.1 but I still can't see the packed movies.

Any ideas how to solve this issue?

Thans in advance!

---

### Post by vapor0 on 2013-03-27
sudo apt-get install rar unrar

---

### Post by ogoun on 2013-03-27
These packages are already installed and I can unpack the archived movies.
```

$ dpkg --get-selections | grep rar
rar                        install
unrar                        install
```

\edit: upnp seems to be the problem. If I mount the NAS within my home folder and use this as a video source in xbmc everything works (althoug in xbmc it doesn't work to use the NFS source and I have to browse the mount point directly).

---

### Post by MacOsX74 on 2013-03-29
> **ogoun said:**
> Hi,

I just noticed that under Ubuntu XBMC can't see the movies packed in rar archives. The XBMC wiki says:



I then added the official PPA ppa:team-xbmc/ppa and installed XBMC 12.1 but I still can't see the packed movies.

Any ideas how to solve this issue?

Thans in advance!

Use this one instead. ppa:nathan-renniewaldock/xbmc-stable. It has rar support.

---


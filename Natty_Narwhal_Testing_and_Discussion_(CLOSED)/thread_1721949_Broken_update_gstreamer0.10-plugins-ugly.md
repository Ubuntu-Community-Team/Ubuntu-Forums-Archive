---
title: "Broken update: gstreamer0.10-plugins-ugly"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-04-05
broken update for gstreamer

```
E: /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_i386.deb:
trying to overwrite `/usr/share/locale/af/LC_MESSAGES/.mo', which is also in package gstreamer0.10-plugins-bad 0.10.21-1ubuntu10
```

```
/var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.17-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mdhollis on 2011-04-05
I'm having the same issue.  When I tried to report it to launchpad aptd crashed. (Bug 741370) aptd crashed with OSError in _copy_io_master(): [Errno 9] Bad file descriptor

---

### Post by mu3en on 2011-04-05
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly0.10/+bug/751343](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly0.10/+bug/751343)

---

### Post by lucazade on 2011-04-05
lots of duplicates :D

---

### Post by zika on 2011-04-05
Does this makes the problem only in 386 branch or in both (386 and amd_64)...?
I'm having this package in update queue... (amd_64)...

P.S.: I've just read: [http://ubuntuforums.org/showthread.php?p=10640565#post10640565](http://ubuntuforums.org/showthread.php?p=10640565#post10640565)... It seems amd_64 is, laso, affrected. I'll wait until it is resolved. Thank You for heads_up...

---

### Post by cecilpierce on 2011-04-05
I had the same problem with synaptic, tried apt-get and it installed OK !!!  :confused:

---

### Post by zika on 2011-04-05
> **cecilpierce said:**
> I had the same problem with synaptic, tried apt-get and it installed OK !!!  :confused:It seems that new version is released... I'll wait until I see it on the list...

---

### Post by encefalocardia on 2011-04-05
Use aptitude safe upgrde.

---

### Post by zika on 2011-04-05
> **encefalocardia said:**
> Use aptitude safe upgrde.For years I've not used (almost) anything but aptitude safe-upgrade... So, You think I do not have to wait until gst-plugins-ugly0.10 (0.10.17-1ubuntu2) comes around...? I'm not in a hurry, I'll, probably, wait... :)

---

### Post by julianb on 2011-04-05
i personally have not used aptitude safe-upgrade but i will if that's what will best prevent breakage.

FYI i was able to get my system fully updated by doing

sudo apt-get update && sudo apt-get dist-upgrade

...
i think the repo's just got updated with the fix.

---

### Post by dino99 on 2011-04-05
now fixed by gstreamer* packages uploaded few minutes ago from main server

---

### Post by lucazade on 2011-04-05
thanks..marks as solved.

---


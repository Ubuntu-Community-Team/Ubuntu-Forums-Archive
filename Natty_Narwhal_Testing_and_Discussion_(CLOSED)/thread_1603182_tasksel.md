---
title: "tasksel"
date: 2010-10-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2010-10-22
```
The following partially installed packages will be configured:
  tasksel 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up tasksel (2.84ubuntu1) ...
Template parse error near `Description-sr@latin.UTF-8: Izaberite softver za instaliranje:', in stanza #1 of /var/lib/dpkg/info/tasksel.templates
dpkg: error processing tasksel (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 tasksel
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tasksel (2.84ubuntu1) ...
Template parse error near `Description-sr@latin.UTF-8: Izaberite softver za instaliranje:', in stanza #1 of /var/lib/dpkg/info/tasksel.templates
dpkg: error processing tasksel (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 tasksel
```

[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/665178](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/665178)

---

### Post by zika on 2010-10-23
Fix released... In a way... :)
&#8222;I don't expect many people to be running Natty just yet&#8220;... :(
Still not marking it solved...

---

### Post by plun on 2010-10-23
It seems to be a Debian trouble with this bug which fails

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=600104](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=600104)

I just removed the sr@latin definition from the template and it was OK for me... but I am not from Serbia...;)

Nevertheless a Ubuntu bug-report must be filed and maybe linked to Debian upstream.

---

### Post by zika on 2010-10-23
> **plun said:**
> It seems to be a Debian trouble with this bug which fails

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=600104](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=600104)

I just removed the sr@latin definition from the template and it was OK for me... but I am not from Serbia...;)

Nevertheless a Ubuntu bug-report must be filed and maybe linked to Debian upstream.
I do not use localized Ubuntu, so I'm fine... :)

---


---
title: "python-freevo Error while trying to install Freevo"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by samuraix51 on 2008-02-11
I'm trying to install freevo on Feisty and am having issues.
I followed the following instructions here: 
[http://doc.freevo.org/FreevoAptUbuntut]("http://doc.freevo.org/FreevoAptUbuntu")

After I've apt-get updated and installed the geole-keyring I try to do
```
sudo apt-get install freevo
``` and it gives me the following error:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freevo: Depends: python-freevo (>= 1.7.3-0ubuntu1) but it is not going to be installed
E: Broken packages
link@zelda:/etc/apt#

```

I've tried ```
sudo apt-get install python-freevo
``` but it comes back with the same error message with different packages though.

I had freevo installed on this same box with feisty before, I had to reformat it and now it won't install it at all.

Upgrading to Gutsy is not an option at the moment as it messes up something with my video card and playing videos.

Anyone have any ideas of what to try?

---

### Post by jurgen32 on 2008-02-12
Good morning.
I saw your topic yesterday (late on the evening).
I am trying to get freevo to work on my Gutsy.

I did'nt have a python error.
Can it be that you did not what long enough with updating after you edit the geol repos?
I did sudo apt-get update and went to bed because it was taking very long.
Maybe he did not get al the packages?

Good luck
Jurgen

By the way: Freevo works on my computer  \\:D/ but I stil have a error something to do with the record_client :?

---


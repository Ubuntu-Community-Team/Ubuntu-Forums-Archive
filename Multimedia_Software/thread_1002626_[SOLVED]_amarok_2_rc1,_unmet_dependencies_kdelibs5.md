---
title: "[SOLVED] amarok 2 rc1, unmet dependencies: kdelibs5 (&amp;gt;= 4:4.1.3) but 4:4.1.2-0ubuntu1"
date: 2008-12-05
forum: Multimedia Software
---

### Post by hachel on 2008-12-05
hello,
I tried to install the new amarok rc, by adding this line to my sources:
```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
``` and then executing
```
sudo apt-get install amarok-kde4
```
as seen in some threads (which themselves mostly refered to here: [http://www.kubuntu.org/amarok2-beta2](http://www.kubuntu.org/amarok2-beta2))

however, first of all it won't appear in synaptic (wouldn't be a bother, just curious), but it won't install via apt-get install, stating the following error:
```
The following packages have unmet dependencies:
  amarok-kde4: Depends: kdelibs5 (>= 4:4.1.3) but 4:4.1.2-0ubuntu11 is to be installed
E: Broken packages

```
any help?
thanks


EDIT: I enabled the prereleased and unsupported updates in the softwaresources and then i was able to update kdelibs and subsequently amarok to v2

---


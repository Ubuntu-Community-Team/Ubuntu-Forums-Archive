---
title: "Cannot update"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2010-08-31
Trying to update Maverick - new installation, but can't update. here is my sources.list ```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100803.1)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ru.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ru.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick universe
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ru.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

The funny things is that all updates are shown - several MBS - but that the Update Manager says there is one 1KB to update as Download size. When I update I get an error saying there is a possible software conflict: ```
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```with details:libgirepository1.0-1 Any ideas what I am missing?

---

### Post by ranch hand on 2010-08-31
That looks fine but what is the problem you are  having?  Did yo run;
```

sudo apt-get update

```
which will update your package list and follow that with;
```

sudo apt-get upgrade

```
which will install any packages that have been changed?

If so post the errrors if it is not upgrading.

---

### Post by Stoneface on 2010-08-31
@ Ranch hand. Did a ```
sudo dpkg --configure -a
``````
sudo apt-get install -f
``````
sudo apt-get dist-upgrade
``` And upgrade is in progress now. Thanks for the reply!

---

### Post by ranch hand on 2010-08-31
Ah, I couldn't figure out what your problem was.  Sorry it is 2 in the morning and maybe I am just slow.

Those commands generally shake things loose for sure.

---

### Post by dino99 on 2010-08-31
might be a server issue (ru), try with main server instead (remove ru. into synaptic repo tab), then update

---


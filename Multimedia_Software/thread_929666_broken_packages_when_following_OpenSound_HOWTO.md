---
title: "broken packages when following OpenSound HOWTO"
date: 2008-09-25
forum: Multimedia Software
---

### Post by carpii on 2008-09-25
Im trying to install OSS, by following the instructions here

[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

But apt-get is complaining about broken packages. 

```

carpii@laramie:~$ sudo apt-get install -y build-essential binutils linux-headers-`uname -r` gawk libtool libesd0 libgtk2.0-dev mercurial libssl-dev
[sudo] password for carpii: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binutils is already the newest version.
linux-headers-2.6.24-21-generic is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
carpii@laramie:~$ 
```


Ive tried to trace where the problem is, and I think its libstdc++6-4.2-dev

```

carpii@laramie:~$ sudo apt-get install g++-4.2
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

The following packages have unmet dependencies.
  g++-4.2: Depends: gcc-4.2 (= 4.2.3-2ubuntu7) but 4.2.4-1ubuntu1 is to be installed
           Depends: gcc-4.2-base (= 4.2.3-2ubuntu7) but 4.2.4-1ubuntu1 is to be installed
           Depends: libstdc++6-4.2-dev (= 4.2.3-2ubuntu7) but it is not going to be installed
E: Broken packages

```

Is this a known problem, or does it suggest Ive somehow messed up my install?

---

### Post by pytheas22 on 2008-09-25
It looks like perhaps your sources list is a bit messed up.  What is the output of:

```
cat /etc/apt/sources.list
```

---

### Post by carpii on 2008-09-26
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by pytheas22 on 2008-09-26
I don't see anything that stands out as a definite problem in that list, but it is a little messy (some redundancy issues etc.).  Here's my list, which works fine:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
deb http://apt.wicd.net hardy extras
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
```

You may want to try replacing your /etc/apt/sources.list file with mine (back yours up first by saving a copy to another location), then run:
```

sudo apt-get update
```

to update your repositories.  Does that make a difference?

---


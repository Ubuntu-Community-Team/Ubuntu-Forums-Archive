---
title: "Error in update manager"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by andahunter on 2009-03-12
Please help. I get this error message when ever i wanna update my system
[IMG]http://img11.imageshack.us/img11/5913/errorz.jpg[/IMG]

Tnx ahead.:)

---

### Post by whoop on 2009-03-12
Are you still using gutsy? It is nearly end of life. If not check /etc/apt/sources.list for gutsy entries and comment them out (or change them to your current ubuntu version when it is not creating duplicate entries).

If you are still using gutsy look for duplicate entries in /etc/apt/sources.list.

---

### Post by andahunter on 2009-03-12
> **whoop said:**
> Are you still using gutsy? It is nearly end of life. If not check /etc/apt/sources.list for gutsy entries and comment them out (or change them to your current ubuntu version when it is not creating duplicate entries).

If you are still using gutsy look for duplicate entries in /etc/apt/sources.list.

Tnx for info, will check on that, P. S. u can c that im using hardy now...

---

### Post by andahunter on 2009-03-12
Cos i dont want to get my sources.list ****ed up this is all i have in it.
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://rs.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe
# Line commented out by installer because it failed to verify:
# deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
# Line commented out by installer because it failed to verify:
deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://rs.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://rs.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://rs.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted

#Eternal Lands package repository
# deb http://ppa.launchpad.net/pjbroad/ubuntu main exis

#Eternal Lands package repository
deb http://ppa.launchpad.net/pjbroad/ubuntu main aptitude update aptitude install eternallands exis

#Eternal Lands package repository
# deb http://ppa.launchpad.net/pjbroad/ubuntu main aptitude update aptitude install eternallands exit

#Eternal Lands package repository
# deb http://ppa.launchpad.net/pjbroad/ubuntu main aptitude update aptitude install eternallands exit

#Eternal Lands package repository
# deb http://ppa.launchpad.net/pjbroad/ubuntu main aptitude update aptitude install eternallands exit
```
Also i dont use eternal lands anymore

---

### Post by whoop on 2009-03-12
This is a sources.list from a hardy desktop I have sitting around. Back up your old one and try this one:
```

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy universe
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Or compare them might want to replace "nl" with "rs"

---

### Post by andahunter on 2009-03-13
Tnx...

---


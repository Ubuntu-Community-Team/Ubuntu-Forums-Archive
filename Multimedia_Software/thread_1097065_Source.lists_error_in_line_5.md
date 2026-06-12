---
title: "Source.lists error in line 5"
date: 2009-03-15
forum: Multimedia Software
---

### Post by Botbob89 on 2009-03-15
Hi guys, when I try to update through the synaptic package manager OR terminal, I am told that I have an error in line 5 of my source.list. Could you guys have a look please :D

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb Index of /ubuntu intrepid main restricted
deb-src Index of /ubuntu intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb Index of /ubuntu intrepid-updates main restricted
deb-src Index of /ubuntu intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb Index of /ubuntu intrepid universe
deb-src Index of /ubuntu intrepid universe
deb Index of /ubuntu intrepid-updates universe
deb-src Index of /ubuntu intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb Index of /ubuntu intrepid multiverse
deb-src Index of /ubuntu intrepid multiverse
deb Index of /ubuntu intrepid-updates multiverse
deb-src Index of /ubuntu intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb Index of /ubuntu intrepid-backports main restricted universe multiverse
# deb-src Index of /ubuntu intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb Index of /ubuntu intrepid partner
# deb-src Index of /ubuntu intrepid partner

deb Index of /ubuntu intrepid-security main restricted
deb-src Index of /ubuntu intrepid-security main restricted
deb Index of /ubuntu intrepid-security universe
deb-src Index of /ubuntu intrepid-security universe
deb Index of /ubuntu intrepid-security multiverse
deb-src Index of /ubuntu intrepid-security multiverse
deb Index of /apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
```

---

### Post by taurus on 2009-03-15
Actually, it's not line 5 that is wrong.  It's the whole entire /etc/apt/sources.list.  Your /etc/apt/sources.list should look something like this

```

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted

```
not 

```

deb **[COLOR="Red"]Index of [/COLOR]**/ubuntu intrepid main restricted

```

---

### Post by Botbob89 on 2009-03-15
Ah thanks :) That makes sense now

The source.list has been given me problems for the past week or so, so I decided to replace it, and that has obviously not worked....

I'm not too sure where to go from here though...?

---

### Post by taurus on 2009-03-15
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and replace all the **index of** with **[http://archive.ubuntu.com](http://archive.ubuntu.com)** so that each line would look something like this now except the last line since it's wine.

```
deb http://archive.ubuntu.com/ubuntu/
```

Or just delete everything in there and paste these in instead.

```

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb Index of /ubuntu intrepid-backports main restricted universe multiverse
# deb-src Index of /ubuntu intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security universe
deb http://security.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security multiverse

deb http://wine.budgetdedicated.com/apt intrepid main

```
Then save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Botbob89 on 2009-03-15
OK I'll do that then :)

Thanks for helping

---


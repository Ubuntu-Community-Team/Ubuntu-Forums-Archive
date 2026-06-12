---
title: "Installing mplayer / realplayer in edgy"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by Fíona on 2007-03-02
Is it not possible to install mplayer and realplayer using apt-get install?

when I try I get the following:

fiona@server:~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
fiona@server:~$ sudo apt-get install realplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

My /etc/apt/sources.list is:

fiona@server:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


I've seen packages for mplayer and realplayer for dapper but not for edgy.

I want to install these packages. How?

---

### Post by taurus on 2007-03-02
Looks like you also need the multiverse as well.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Fíona on 2007-03-02
Thank you for your reaction taurus. I realised I needed multiverse but thought that backport multiverse was the one I needed.

Mplayer seems to have installed OK, but with realplayer I get this:

fiona@server:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate

Is realplayer then, not available via apt-get/

---

### Post by taurus on 2007-03-02
Here you go for RealPlayer.

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

---

### Post by Fíona on 2007-03-02
Thanks  taurus for pointing me in the right direction.

---

### Post by cari on 2008-04-03
Bah! with every clean install I mess with this.. Had the same problem, all sources "ticked" but couldn't install mplayer.

So finally I (re)found out that you have to enable them (multiverse etc) via the "Add" button:)

Just in case I should go through a clean install sometimes soon.

BTW: source-o-matic hasn't been around for a while. Such a shame

---


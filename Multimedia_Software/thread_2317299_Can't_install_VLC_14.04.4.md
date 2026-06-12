---
title: "Can't install VLC: 14.04.4"
date: 2016-03-15
forum: Multimedia Software
---

### Post by Bucky Ball on 2016-03-15
Hi all,

Running Xubuntu 14.04.4 on a HP Sream 11. 

```
$ uname -a
Linux Bluey 3.16.0-67-generic #87~14.04.1-Ubuntu SMP Fri Mar 11 00:26:02 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty
```

(Strange thing is I have 14.04.4 on another box and it is 3.13.0.79.)

When I try to install VLC I get this:

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.1.6-0ubuntu14.04.1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.1.6-0ubuntu14.04.1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.1.6-0ubuntu14.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Found plenty of users with the problem but most of them fixed with a black magic combination of these commands:

```
sudo apt-get remove --purge vlc-nox
 sudo apt-get autoclean
 sudo dpkg --configure -a
 sudo apt-get -f install
 sudo apt-get autoremove
 sudo apt-get update
 sudo apt-get dist-upgrade
 sudo apt-get install vlc
```

... [from here]("http://askubuntu.com/questions/666219/vlc-fails-to-install-on-14-04"), not necessarily in that order, but a combination thereof. No luck here. Keen to get this working as the plan was to give a presentation with this machine next week and need VLC to do so. Parole also won't install complaining of similar issues:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 parole : Depends: gstreamer1.0-libav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Trying to install directly from official repos using command line and Synaptics. Synaptics reports broken packages, fixes, but then won't install. Circular. Tried from the VLC daily PPA. Same result.

```
# deb cdrom:[Xubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty main restricted
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-updates main restricted
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty universe
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty universe
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-updates universe
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty multiverse
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty multiverse
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-updates multiverse
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-backports main restricted universe multiverse
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-backports main restricted universe multiverse

deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-security main restricted
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-security main restricted
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-security universe
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-security universe
deb http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-security multiverse
deb-src http://mirror.aarnet.edu.au/pub/ubuntu/archive/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main
```

Hair pulling. Torrenting xubuntu-core 15.10 now out of desperation but rather not go that route. :| TIA.

---

### Post by mc4man on 2016-03-15
Remove vlc-data to fully remove all vlc packages.
Maybe install & use aptitude to try to install vlc, it's generally more verbose as to what's blocking the install

---

### Post by Bucky Ball on 2016-03-15
Ha! No sooner did I post this thread than I opened Synaptics and looked for 'gstreamer1.0-libav', what it was moaning about in the Parole error.

There was a version installed called 'gstreamer1.0-libav:i386' and the one I was looking for not installed. After a bit of a battle trying to uninstall one and install the other, I finally got there and then installed Parole and VLC without issue. The wonders of modern technology. Solved.

Well, guess this might be handy for anyone who can't get it fixed the way that is suggested on 99% of the websites they're going to find. :)

---

### Post by linuuxi on 2016-03-17
Same problem here. Didn't know the solution.

Thanks for the solution. :)

---


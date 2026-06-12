---
title: "Problem installing audacity"
date: 2011-06-28
forum: Multimedia Software
---

### Post by mamboze on 2011-06-28
Hi,

I've got a problem installing audacity on my Samsung RV511 laptop, OS 10.04. Here's the terminal dialog
```
~$ sudo apt-get install audacity
[sudo] password for roy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  audacity: Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installable or
                     libjack-0.116 but it is not installable
            Recommends: libavformat52 (>= 5:0.6~svn20100726) but it is not going to be installed
E: Broken packages

```

I installed audacity on a desktop, also 10.04, about a year ago. No problem there. 

Any suggestions?

---

### Post by wolfen69 on 2011-06-28
Try
```
sudo apt-get install -f
```
then
```
sudo apt-get update
```

---

### Post by mamboze on 2011-06-29
OK, I ran both commands and then tried 'sudo apt-get install audacity', but got the same output as before. I looked around online but haven't found anything specific on this issue.

---

### Post by wolfen69 on 2011-06-29
Do you have the proper repos enabled? Open synaptic and go to settings>repositories>ubuntu software and other software to see if you have all repos enabled.

---

### Post by mamboze on 2011-06-29
Thanks for your help.

OK so far, I checked settings>repositories for ubuntu (canonical) repos and they seem to be all there. 

And, using synaptic, audacity is listed there. But when an install is attempted, it gives this error message. 

```
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. 
Make sure that all required repositories are added and enable in the preferences

Depends libjack-jack2.0(>=1.9.5~dfsg-14) but it is not installable or libjac-0.116 but it is not installable
Recommends: libavformat52 but it is not going to be installed

```
I checked 'Installable from CD-ROM/DVD' but this made no difference.

---

### Post by wolfen69 on 2011-06-30
Please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by mamboze on 2011-07-01
Sorry for the delay in replying  :)

```
:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb http://www.debian-multimedia.org stable main non-free

```

---

### Post by mamboze on 2011-07-03
OK, I've come to the end of the line on this one. I posted on the Audacity forum 

[http://forum.audacityteam.org/viewtopic.php?f=18&t=58330](http://forum.audacityteam.org/viewtopic.php?f=18&t=58330)

and I was told it was a ubuntu problem. Apparently, they just supply the source code. 

So, if the Audacity package is broken, as seems to be the case, why is it still in the repos? What's the procedure for reporting a broken package? The only option I can think of is to install Audacity with VirtualBox as a windows app. But I'm reluctant to do that. 

I would like very much to install Audacity as a Linux package. So any help, suggestions etc would be most welcome.

---

### Post by CatKiller on 2011-07-03
Comment out the Debian line that you've put in there and reload. Debian and Ubuntu are not the same.

---

### Post by mamboze on 2011-07-04
Thanks for your help but I'm not sure which line you're referring to.

---

### Post by CatKiller on 2011-07-04
> **mamboze said:**
> Thanks for your help but I'm not sure which line you're referring to.
The one at the end. The one that you've added, and the only one with the word Debian in.

You may still have dependency problems from packages that you've already installed from that repository. If you want to add multimedia packages that aren't in the normal repositories, Medibuntu is compatible with the normal repositories. But get your current dependency problems sorted out before you go adding any more.

---

### Post by mamboze on 2011-07-07
CatKiller, thanks very much, that worked. Another step towards Linux enlightenment :D

---


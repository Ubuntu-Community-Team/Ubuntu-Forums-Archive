---
title: "[B]Cant Update Xubuntu Please Help![/B]"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by BigRock on 2009-01-11
[B]Hello,
i am having problems with updating my Xubuntu version 7.10 to version 8.04 
it starts updating, and gets to the second stage. then an error message comes up,,,[/B]

Can't install 'xubuntu-desktop'

It was impossible to install a required package. Please report this as a bug. 

**When i push 'Close' on that window, an extra window comes up that says:**

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

[B]Also, My internet icon says that there is no network connection even though i can go on the internet and it works perfectly, maybe this could be the cause of the problem??
Please help.

Thanks,
BigRock[/B]

---

### Post by albinootje on 2009-01-11
> **BigRock said:**
> [B] i am having problems with updating my Xubuntu version 7.10 to version 8.04 
it starts updating, and gets to the second stage. then an error message comes up,,,[/B]

Can't install 'xubuntu-desktop'

It was impossible to install a required package. Please report this as a bug. 


Can you post the output of the following :
```

cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install xubuntu-desktop

```

---

### Post by BigRock on 2009-01-17
> **albinootje said:**
> Can you post the output of the following :
```

cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install xubuntu-desktop

```

Okay this is what i got for cat /etc/apt/sources.list:

root@turbo-desktop:/home/turbo# cat /etc/apt/sources.list:
cat: /etc/apt/sources.list:: No such file or directory
root@turbo-desktop:/home/turbo# 
root@turbo-desktop:/home/turbo# 

for sudo apt-get update i got:

root@turbo-desktop:/home/turbo# sudo apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release powerpc+ps3 (20071016) gutsy/main Translation-en_GB
Reading package lists... Done

An&#273; for sudo apt-get install xubuntu-desktop i got:

sudo apt-get install xubuntu-desktop


Please Help Me :( i hav no idea what is happening

---

### Post by BigRock on 2009-01-17
Sorry for the end of my last post

for sudo apt-get install xubuntu-desktop i got:

root@turbo-desktop:/home/turbo# sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@turbo-desktop:/home/turbo#

---

### Post by albinootje on 2009-01-17
> **BigRock said:**
> Okay this is what i got for cat /etc/apt/sources.list:

root@turbo-desktop:/home/turbo# cat /etc/apt/sources.list:
cat: /etc/apt/sources.list:: No such file or directory

With copy&paste you mistakenly added a ":" sign in the end it looks like.

You're on a ps3, correct ?

---

### Post by BigRock on 2009-01-17
> **albinootje said:**
> With copy&paste you mistakenly added a ":" sign in the end it looks like.

You're on a ps3, correct ?

Yes that is correct

---

### Post by BigRock on 2009-01-17
> **albinootje said:**
> With copy&paste you mistakenly added a ":" sign in the end it looks like.

You're on a ps3, correct ?

i did it again this is what i got

turbo@turbo-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release powerpc+ps3 (20071016)]/ gutsy main
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-backports main restricted universe multiverse
# deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security main
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security multiverse

---

### Post by albinootje on 2009-01-17
> **BigRock said:**
> i did it again this is what i got
turbo@turbo-desktop:~$ cat /etc/apt/sources.list

Thanks.

See here :
[http://ubuntu-tutorials.com/2008/04/23/how-to-upgrade-ubuntu-710-to-ubuntu-804/](http://ubuntu-tutorials.com/2008/04/23/how-to-upgrade-ubuntu-710-to-ubuntu-804/)

If that doesn't work, can you run this from a terminal :
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo update-manager --dist-upgrade

```

---


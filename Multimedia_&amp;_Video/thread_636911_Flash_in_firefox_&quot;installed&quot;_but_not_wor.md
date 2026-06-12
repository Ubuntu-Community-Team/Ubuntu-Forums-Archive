---
title: "Flash in firefox &quot;installed&quot; but not working"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by oddworld on 2007-12-10
Trying to get flash working in firefox. 
I installed everything I would need in automatix.
After going to youtube I get a message I need to install flash. 
After clicking on adobe non-free flash it tells me: "package flashplayer -nonfree is already installed" restart firefox for it to work.
Well I have done that many many times and it refuses to work.
I tried:

```

davis@davis-laptop:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplayer-mozilla is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplayer-mozilla has no installation candidate
davis@davis-laptop:~$

```


my sources.list:

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://packages.medibuntu.org/ gutsy free non-free


#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

```
 


My firefoxrc:
```

# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.

```

---

### Post by oddworld on 2007-12-10
SOLVED:

I dont know why this worked, but going to:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and getting flash straight from adobe solved the problem.
Weird...

I thought automatix or mozilla or synaptic would have done the job, but what finally worked was me downloading the tar.bz

---

### Post by Martin Witte on 2007-12-10
the package you're looking for is called 'flashplugin-nonfree', in the multiverse repositories

---

### Post by NilsE on 2007-12-10
The flash player in the repos is not working due to a bug in the checksum. Don't know when it will be fixed but in the mean time you can download this deb file and install it 

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

---

### Post by Jeanpaul145 on 2007-12-10
> **NilsE said:**
> The flash player in the repos is not working due to a bug in the checksum. Don't know when it will be fixed but in the mean time you can download this deb file and install it 

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

I have this same problem, so thank you for the info!:guitar: (I'm one of those people who like to know WHAT is wrong when something is not working as it should:popcorn:)

I used the package you supplied, and I didn't even need to restart firefox to use the plugin (I tested it on youtube).

---

### Post by oddworld on 2007-12-10
> **NilsE said:**
> The flash player in the repos is not working due to a bug in the checksum. Don't know when it will be fixed but in the mean time you can download this deb file and install it 

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Gotta love those debs!

---

### Post by daradib on 2007-12-10
See this for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---


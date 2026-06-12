---
title: "Skype dependences"
date: 2010-05-17
forum: Multimedia Software
---

### Post by Guyik on 2010-05-17
Hi everyone,

Yesterday I achieved my microphone woked, and today I was going to install skype but:

> 
  skype: Depends on: libasound2 (> 1.0.16) but 1.0.15-3ubuntu4 is going to be installed
         Depends on: libgcc1 (>= 1:4.3) but 1:4.2.4-1ubuntu4 is going to be installed
         Depends on: libqt4-dbus (>= 4.4.3) but cannot be installed
         Depends on: libqt4-network (>= 4.4.3) but cannot be installed
         Depends on: libqtcore4 (>= 4.4.3) but cannot be installed
         Depends on: libqtgui4 (>= 4.4.3) but cannot be installed
         Depends on: libstdc++6 (>= 4.3) but 4.2.4-1ubuntu4 is going to be installed
The errors were in Spanish (I'm Spanish), I have translated them (perhaps that's not the exact translation).

How can I update those libraries? I use these repositories (my "/etc/apt/sources.list" file):

> 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main #OpenOffice.org
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
Any Ideas? Could I update that or install an older version of Skype?
Thanks very much.

---

### Post by Xianath on 2010-05-17
It looks like Skype was built against libraries that are more recent than what Hardy has. Since Lucid LTS is out, you may consider upgrading.

---

### Post by ajgreeny on 2010-05-17
The version of skype available for ubuntu on the skype website is for ubuntu 8.10+ so for your 8.04 you may need something earlier from them, though I can not find any way to get an older version.

I have two older versions sitting in a backup of my machine's download folder, 2.0.0.68 and 2.0.0.72, which I would happily let you have if they are of any use.  I downloaded them in Feb 2009, so they are both later than ubuntu 8.04, so may still not work properly.

---

### Post by Guyik on 2010-05-17
> **ajgreeny said:**
> The version of skype available for ubuntu on the skype website is for ubuntu 8.10+ so for your 8.04 you may need something earlier from them, though I can not find any way to get an older version.

I have two older versions sitting in a backup of my machine's download folder, 2.0.0.68 and 2.0.0.72, which I would happily let you have if they are of any use.  I downloaded them in Feb 2009, so they are both later than ubuntu 8.04, so may still not work properly.

I would be very pleased to try those versions in my computer. I have also been looking for older versions of skype, but didn't find anything for linux.

I have thought about installing skype in windows, in a virtual machine, but my webcam doesn't work properly in virtual box.

Could you send those versions to my e-mail address (vero_g.e._@hotmail.com), please?

[I](I know that this is not a forum for learning English but, how can I indicate that I'm going to talk about another topic?)
Do you use any programme or application to backup automatically?
[/I]
Thank you so much for your help.

---

### Post by ajgreeny on 2010-05-17
One version sent as asked.

You will be better to start a new thread on any other subject, but for backups I use grsync/rsync to copy /home to a USB hard disk.

---


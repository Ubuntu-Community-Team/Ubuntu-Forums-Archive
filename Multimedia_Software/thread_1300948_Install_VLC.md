---
title: "Install VLC"
date: 2009-10-25
forum: Multimedia Software
---

### Post by motorhead_1 on 2009-10-25
hi, I've tried to install VLC through the commmand line: sudo apt-get install vlc vlc-plugin-pulse
it didn't work;  
```
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vlc has no installation candidate
```
I cannot install it from Synaptic since it's not there...

---

### Post by fancypiper on 2009-10-25
Try adding more software sources.  I think it is community supported.  From Synaptic: Canonical does not provide updates for vlc. Some updates may be provided by the Ubuntu community.

---

### Post by motorhead_1 on 2009-10-25
I didn't have 'multiverse' repositories enabled now I do but I still cannot find VLC...
do I have to add a line to the source list? I'm sorry I'm a totally newbie

---

### Post by vinutux on 2009-10-25
install it from add/remove or synaptic

---

### Post by fancypiper on 2009-10-25
[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683)

On second thought, I think medibuntu has it. Add the medibuntu sources.

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

---

### Post by sgosnell on 2009-10-25
If you have the Jaunty multiverse repository enabled, vlc should show up in Synaptic.  If you want to use a ppa, see [this page](http://www.videolan.org/vlc/download-ubuntu.html).

You do have to refresh the sources after changing the repositories, in Synaptic click on Reload, or from a terminal, "sudo apt-get update".

---

### Post by motorhead_1 on 2009-10-25
medibuntu sources have been already added..  multiverse repository are enabled  although VLC doesn't show up...

here's is my source list

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates universe
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty multiverse
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
```

---

### Post by motorhead_1 on 2009-10-25
I've enabled universe and main repositories sources and then I've been abe to find VLC and install it.

---

### Post by sgosnell on 2009-10-25
No, the multiverse repository is still commented out.  Security multiverse isn't the same thing.

---

### Post by motorhead_1 on 2009-10-26
> **sgosnell said:**
> No, the multiverse repository is still commented out.  Security multiverse isn't the same thing.
I thought it was enabled, how can I do it? it can be useful for the next time.

[[IMG]http://img39.imageshack.us/img39/9320/screenshotmj.th.png[/IMG]](http://img39.imageshack.us/i/screenshotmj.png/)

---

### Post by sgosnell on 2009-10-26
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) jaunty multiverse

The # at the beginning of the line makes it a comment, and not active.  Remove the # and the repository will be active after you do a reload/update.

---


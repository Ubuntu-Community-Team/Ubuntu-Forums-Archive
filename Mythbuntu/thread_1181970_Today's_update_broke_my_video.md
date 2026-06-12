---
title: "Today's update broke my video"
date: 2009-06-08
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-08
Just did the dist-upgrade to install the 10 package updates to nvidia vdpau and mythtv then rebooted.  Upon startup my X fails to initialize and dumps me into Safe Mode.  The Xorg.0.log says:

(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

However when I do an lsmod |grep nv I get:

nvidia               7238628  0 
agpgart                42696  1 nvidia

Except for a database package error (see other thread for that), the update gave no failures or errors.  My xorg.conf that was working this morning before the package upgrades has not changed and looks fine.

What can I do to get things working again and is the update broken?

---

### Post by bcg30506 on 2009-06-08
I got it fixed.  Looks like a dependency was missed in the updated packages.  I had to manually install the nvidia-glx-185 kernel module package and the kernel source, nvidia-185-kernel-source, and nvidia-185-modaliases.  For some reason apt-get did not automatically detect and update these.  Once I manually installed them and rebooted, my video was back.

However, it did break one setting: Everything was blue.  The Hue had been reset to 0% so the colors were all wrong.  I set it back to 50% (talking about within myth's internal player) and this fixed the color.

---

### Post by superm1 on 2009-06-09
Where are you getting the -185 driver?  It's not in the repos yet I thought.

---

### Post by bcg30506 on 2009-06-09
It's in the mythbuntu repo according to my setup.  It showed up in my motd as an available upgrade.  Here is my sources.list:

# deb cdrom:[Mythbuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

deb [http://ppa.launchpad.net/ripps818/ppa/ubuntu](http://ppa.launchpad.net/ripps818/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ripps818/ppa/ubuntu](http://ppa.launchpad.net/ripps818/ppa/ubuntu) jaunty main

---

### Post by jbman on 2009-06-09
i installed them on the weekend, found 185 is causing tearing even with the no composite in xorg even though the new driver says its not needed anymore.

Also I have seen a bug report in trac that its causing some machines to hard lock up with h264 media playback.

---

### Post by bcg30506 on 2009-06-09
That's odd.  I'm not seeing any problems now.  No tearing (I still have Composites disabled in xorg.conf) and no lockups even playing the AVCHD MTS files from our Canon camera (which is a strange version of x264 I think).

---


---
title: "manual update problems"
date: 2009-12-23
forum: Multimedia Software
---

### Post by catman63879 on 2009-12-23
hello, imhaving trouble mau=nually running and update with the update manager. i keep getting this error
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E43D207C62D38753
what the ??

---

### Post by dvlchd3 on 2009-12-23
Every repository in your /etc/apt/sources.list file should have a GPG key associated with it.  This will ensure all downloads from that repository are authentic.

Have you added any additional repositories besides the ones that came with the default install.  There are four ways to add them:

Through Synaptics (Settings -> Repositories)
Through the "Software Sources" Under the System -> Administration menu.
Adding lines to the /etc/apt/sources.list file
Adding a new file to /etc/apt/sources.list.d/ directory.

This would be the reason, and hopefully wherever you found out about the repository/software should have some information on how to add the GPG key.  Otherwise, post your /etc/apt/sources.list file, and any files in the /etc/apt/sources.list.d/ folder so we can try to figure out which GPG key you need.

---

### Post by catman63879 on 2009-12-24
far as i know i havent installed anything except for the routine updates that occur by itself nor have i added anything. im still reeeeally new to ubuntu and havent had any major problems until now, which is still no biggie, i can just stay away from vh1.com

---

### Post by catman63879 on 2009-12-24
ok took me a while to get my head together heres my sources.list file

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) jaunty main
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

---

### Post by Goyo on 2009-12-26
> deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) jaunty main
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

For sure this lines are not added by a default Ubuntu install nor by routine updates.

The PPA for handbrake shows how to add the gpg key:

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 62D38753
```

---

### Post by catman63879 on 2009-12-27
problem solved, Thanx goyo!!

---


---
title: "Miro Installation Problem"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by Tom B on 2008-02-23
A while ago, in the update manager there was an option to "update" miro to an older version. I thought it was strange, especially because I couldn't select the update so it just sat there. Then I started having some problems with Miro. I decided to try to reinstall it. I uninstalled it, then when I went to reinstall I got an error: 

"Depends: libboost-date-time1.33.1  but it is not installable

 Depends: libboost-filesystem1.33.1  but it is not installable

 Depends: libboost-python1.33.1  but it is not installable

 Depends: libboost-thread1.33.1  but it is not installable

 Depends: libxine-main1 (>=1.1.1) but it is not installable

  Depends: python (<2.5) but 2.5.1-1ubuntu2 is to be installed
 
 Depends: mozilla-psm  but it is not installable"


I checked the packages- i have 1.34.x of the libboost ones installed, a package called python2.4 and the python package version 2.5, and I couldn't find mozilla-psm. I have checked my repositories and cannot figure out what is wrong, and now I am without Miro, which I have come to love recently. Any ideas?

---

### Post by taurus on 2008-02-23
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Tom B on 2008-02-23
I've been messing around with the repositories, so more than likely something is messed up by now, but I don't know enough to know what.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports restricted multiverse main universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) dapper/
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) gutsy multiverse
deb [http://ppa.launchpad.net/luks/ubuntu](http://ppa.launchpad.net/luks/ubuntu) gutsy main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed multiverse restricted main universe

---

### Post by Tom B on 2008-02-25
I have been messing around with the repositories some more, adding and removing the Miro one and others. Now when I try to install Miro I get "Depends: libxine1 (<1.1.8 ) but 1.1.10-1~gutsy1 is to be installed" but when I force libxine1 to 1.1.7 it removes libxine1 plugins. Then when I try to install Miro, it says it depends on them but they are not to be installed. Any ideas?

---

### Post by Tom B on 2008-02-29
I got some help with this on the Miro forums, where some other people are having the same problem. It comes from an issue with the newest version of libxine causing Miro to crash when it plays videos. You have to disable backports in order to get the old version of libxine that works with Miro. Here's what I had to do to fix it (on Gutsy). (I don't know if this is good advice for everybody, it just worked for me.) Go to Synaptic Package Manager and uninstall Miro and Miro-Data. Then go to Settings->Repositories. Go to the "Updates" tab and un-check the "Unsupported updates (Gutsy Backports)" option. Then click "Close" (not "Revert," which will undo your change). Libxine's version will now be marked for an "update" to the right version. Click apply. Once it finishes, mark Miro for installation, and apply. It works!

[Here's the bugzilla link.]("http://bugzilla.pculture.org/show_bug.cgi?id=9614")

---

### Post by utkjamie on 2008-03-02
You have to be careful with downgrading libxine. In my case, it uninstalled a number of packages including Kaffeine and ManDVD. Make sure you note what is being removed during the downgrade so you can re-install the important things afterwards.

---

### Post by go_beep_yourself on 2008-03-03
Solution here:

[http://ubuntuforums.org/showpost.php?p=4444598&postcount=7](http://ubuntuforums.org/showpost.php?p=4444598&postcount=7)

---


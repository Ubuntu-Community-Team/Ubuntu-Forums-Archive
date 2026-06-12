---
title: "Can't install Adobe Reader"
date: 2009-08-06
forum: Multimedia Software
---

### Post by adamthompson on 2009-08-06
I somehow uninstalled Adobe Reader 9. I can't reinstall it using apt. When I try I get this result:

Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

I'm using Hardy 8.04 64-bit, and this my sources.list:

# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2)]/ hardy main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-updates universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy-security multiverse

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) hardy multiverse #Added by software-properties

deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) hardy multiverse

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by stumbleUpon on 2009-08-06
Change 'intrepid' to 'hardy' in the last two lines of your sources.list file and then try again.

---

### Post by LeChacal on 2009-08-07
> First add the repository. Go to System > Administration > Software Sources > Third Party Software Tab and check the [http://archive.canonical.com](http://archive.canonical.com) lines.

Close down Software Sources and start Synaptic (System > Administration > Synaptic Package Manager). Search for package acroread and install it. You'll get Adobe Reader v9.1.2

[http://ubuntuforums.org/showthread.php?t=1230407&highlight=acroread](http://ubuntuforums.org/showthread.php?t=1230407&highlight=acroread)

---

### Post by 73ckn797 on 2009-08-07
> **stumbleUpon said:**
> Change 'intrepid' to 'hardy' in the last two lines of your sources.list file and then try again.


This appears to be the solution after viewing your sources listings.

---


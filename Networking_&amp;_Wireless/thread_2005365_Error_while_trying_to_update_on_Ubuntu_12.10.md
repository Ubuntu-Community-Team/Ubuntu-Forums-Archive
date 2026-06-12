---
title: "Error while trying to update on Ubuntu 12.10"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by jeshrel on 2012-06-17
Hi,

I am trying to update ubuntu 12.10 using the help of terminal using the command "sudo apt-get update" it does not update it points out an error, i have attached a screenshot of the terminal error kindly check it for further reference. When i try updating using update manager it says "Failed to download repository information
 Check your Internet connection."
but my internet connection is working fine
and in details it displays the following

"W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/Release](http://in.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead."

Kindly help

---

### Post by matt_symes on 2012-06-17
Hi

Open a terminal and type

```
grep -r ^ /etc/apt/*
```

Copy and paste the output back here by copying and pasting from the terminal (highlight text->right click->copy) into your next post.

Post the output between code tags like this

[noparse]```
output
```[/noparse]

to get output like this.

```
output
```

Kind regards

---

### Post by alushari on 2012-08-22
Hi I have just upgraded to 12.10 having other third party repositories. I have come across some unsuitabilities, some help would be appreciated.

Here is the code:

```
 that shutdown while a upgrade
/etc/apt/apt.conf.d/50unattended-upgrades:// is running is possible (with a small delay)
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::MinimalSteps "true";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Install all unattended-upgrades when the machine is shuting down
/etc/apt/apt.conf.d/50unattended-upgrades:// instead of doing it in the background while the machine is running
/etc/apt/apt.conf.d/50unattended-upgrades:// This will (obviously) make shutdown slower
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::InstallOnShutdown "true";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Send email to this address for problems or packages upgrades
/etc/apt/apt.conf.d/50unattended-upgrades:// If empty or unset then no email is sent, make sure that you
/etc/apt/apt.conf.d/50unattended-upgrades:// have a working mail setup on your system. A package that provides
/etc/apt/apt.conf.d/50unattended-upgrades:// 'mailx' must be installed. E.g. "user@example.com"
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::Mail "root"
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Set this value to "true" to get emails only on errors. Default
/etc/apt/apt.conf.d/50unattended-upgrades:// is to always send a mail if Unattended-Upgrade::Mail is set
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::MailOnlyOnError "true";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Do automatic removal of new unused dependencies after the upgrade
/etc/apt/apt.conf.d/50unattended-upgrades:// (equivalent to apt-get autoremove)
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::Remove-Unused-Dependencies "false";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Automatically reboot *WITHOUT CONFIRMATION* if a 
/etc/apt/apt.conf.d/50unattended-upgrades:// the file /var/run/reboot-required is found after the upgrade 
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::Automatic-Reboot "false";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Use apt bandwidth limit feature, this example limits the download
/etc/apt/apt.conf.d/50unattended-upgrades:// speed to 70kb/sec
/etc/apt/apt.conf.d/50unattended-upgrades://Acquire::http::Dl-Limit "70";
/etc/apt/apt.conf.d/15update-stamp:APT::Update::Post-Invoke-Success {"touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";};
/etc/apt/apt.conf.d/00trustcdrom:APT::Authentication::TrustCDROM "true";
/etc/apt/apt.conf.d/20dbus:// Notify all clients to reload the cache
/etc/apt/apt.conf.d/20dbus:APT::Update::Post-Invoke-Success { "[ ! -f /var/run/dbus/system_bus_socket ] || /usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged || true"; };
/etc/apt/apt.conf.d/01autoremove:APT
/etc/apt/apt.conf.d/01autoremove:{
/etc/apt/apt.conf.d/01autoremove:  NeverAutoRemove
/etc/apt/apt.conf.d/01autoremove:  {
/etc/apt/apt.conf.d/01autoremove:    "^firmware-linux.*";
/etc/apt/apt.conf.d/01autoremove:    "^linux-firmware$";
/etc/apt/apt.conf.d/01autoremove:    "^linux-image.*";
/etc/apt/apt.conf.d/01autoremove:    "^kfreebsd-image.*";
/etc/apt/apt.conf.d/01autoremove:    "^linux-restricted-modules.*";
/etc/apt/apt.conf.d/01autoremove:    "^linux-ubuntu-modules-.*";
/etc/apt/apt.conf.d/01autoremove:    "^gnumach$";
/etc/apt/apt.conf.d/01autoremove:    "^gnumach-image.*";
/etc/apt/apt.conf.d/01autoremove:  };
/etc/apt/apt.conf.d/01autoremove:
/etc/apt/apt.conf.d/01autoremove:  Never-MarkAuto-Sections
/etc/apt/apt.conf.d/01autoremove:  {
/etc/apt/apt.conf.d/01autoremove:    "metapackages";
/etc/apt/apt.conf.d/01autoremove:    "restricted/metapackages";
/etc/apt/apt.conf.d/01autoremove:    "universe/metapackages";
/etc/apt/apt.conf.d/01autoremove:    "multiverse/metapackages";
/etc/apt/apt.conf.d/01autoremove:    "oldlibs";
/etc/apt/apt.conf.d/01autoremove:    "restricted/oldlibs";
/etc/apt/apt.conf.d/01autoremove:    "universe/oldlibs";
/etc/apt/apt.conf.d/01autoremove:    "multiverse/oldlibs";
/etc/apt/apt.conf.d/01autoremove:  };
/etc/apt/apt.conf.d/01autoremove:};
grep: /etc/apt/auth.conf: Permission denied
/etc/apt/sources.list:# deb cdrom:[Sabily-ultimate 11.04 _Badr_ - i386 (20110505)]/ natty main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu quantal restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu quantal-updates restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from the 'backports'
/etc/apt/sources.list:## repository.
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://ye.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://ye.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu quantal-security restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu natty partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu natty partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-proposed restricted main multiverse universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu quantal-proposed restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu quantal-backports restricted main multiverse universe
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu quantal-backports restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/google-earth.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list.save:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/medibuntu.list.distUpgrade:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list.distUpgrade:deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/medibuntu.list.distUpgrade:# deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/medibuntu.list:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list:deb http://packages.medibuntu.org/ quantal free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin" disabled on upgrade to quantal
/etc/apt/sources.list.d/medibuntu.list:deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/sabily.team-ppa-oneiric.list.distUpgrade:deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/sabily.team-ppa-oneiric.list.distUpgrade:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/google-talkplugin.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save:deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save:deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.distUpgrade:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
/etc/apt/sources.list.d/wuala.list.save:# Wuala repository
/etc/apt/sources.list.d/wuala.list.save:deb http://repo.wuala.com stable main # disabled on upgrade to oneiric disabled on upgrade to precise disabled on upgrade to quantal
/etc/apt/sources.list.d/sabily_team-ppa-natty.list.save:deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/sabily_team-ppa-natty.list.save:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/google-earth.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list.distUpgrade:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to quantal
/etc/apt/sources.list.d/wuala.list:# Wuala repository
/etc/apt/sources.list.d/wuala.list:deb http://repo.wuala.com stable main # disabled on upgrade to oneiric disabled on upgrade to precise disabled on upgrade to quantal
/etc/apt/sources.list.d/medibuntu.list.save:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list.save:deb http://packages.medibuntu.org/ quantal free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin" disabled on upgrade to quantal
/etc/apt/sources.list.d/medibuntu.list.save:deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save:deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to quantal
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.distUpgrade:deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.distUpgrade:deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/google-earth.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/wuala.list.distUpgrade:# Wuala repository
/etc/apt/sources.list.d/wuala.list.distUpgrade:deb http://repo.wuala.com stable main # disabled on upgrade to oneiric disabled on upgrade to precise
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list:deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list:deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/google-talkplugin.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/sabily_team-ppa-natty.list.distUpgrade:deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu natty main
/etc/apt/sources.list.d/sabily_team-ppa-natty.list.distUpgrade:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu natty main
/etc/apt/sources.list.d/sabily.team-ppa-oneiric.list.save:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu precise main # disabled on upgrade to oneiric disabled on upgrade to precise
/etc/apt/sources.list.distUpgrade:# deb cdrom:[Sabily-ultimate 11.04 _Badr_ - i386 (20110505)]/ natty main restricted
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list.distUpgrade:# newer versions of the distribution.
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise main restricted
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list.distUpgrade:## distribution.
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list.distUpgrade:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list.distUpgrade:## review or updates from the Ubuntu security team.
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise universe
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise universe
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-updates universe
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list.distUpgrade:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list.distUpgrade:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list.distUpgrade:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list.distUpgrade:## security team.
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise multiverse
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:## Uncomment the following two lines to add software from the 'backports'
/etc/apt/sources.list.distUpgrade:## repository.
/etc/apt/sources.list.distUpgrade:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list.distUpgrade:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list.distUpgrade:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list.distUpgrade:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list.distUpgrade:## or updates from the Ubuntu security team.
/etc/apt/sources.list.distUpgrade:deb http://ye.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://ye.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list.distUpgrade:## 'partner' repository.
/etc/apt/sources.list.distUpgrade:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list.distUpgrade:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list.distUpgrade:deb http://archive.canonical.com/ubuntu natty partner
/etc/apt/sources.list.distUpgrade:deb-src http://archive.canonical.com/ubuntu natty partner
/etc/apt/sources.list.distUpgrade:
/etc/apt/sources.list.distUpgrade:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list.distUpgrade:## developers who want to ship their latest software.
/etc/apt/sources.list.distUpgrade:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list.distUpgrade:deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
/etc/apt/sources.list.distUpgrade:deb http://archive.ubuntu.com/ubuntu precise-backports restricted main multiverse universe
/etc/apt/sources.list.distUpgrade:deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu precise main
/etc/apt/sources.list.distUpgrade:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu precise main
/etc/apt/sources.list.save:# deb cdrom:[Sabily-ultimate 11.04 _Badr_ - i386 (20110505)]/ natty main restricted
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list.save:# newer versions of the distribution.
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal main restricted
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal main restricted
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list.save:## distribution.
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal-updates main restricted
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list.save:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list.save:## review or updates from the Ubuntu security team.
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal universe
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal universe
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-updates universe
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal-updates universe
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list.save:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list.save:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list.save:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list.save:## security team.
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal multiverse
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal multiverse
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal-updates multiverse
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## Uncomment the following two lines to add software from the 'backports'
/etc/apt/sources.list.save:## repository.
/etc/apt/sources.list.save:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list.save:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list.save:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list.save:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list.save:## or updates from the Ubuntu security team.
/etc/apt/sources.list.save:deb http://ye.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
/etc/apt/sources.list.save:deb-src http://ye.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list.save:deb-src http://archive.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list.save:## 'partner' repository.
/etc/apt/sources.list.save:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list.save:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list.save:deb http://archive.canonical.com/ubuntu natty partner
/etc/apt/sources.list.save:deb-src http://archive.canonical.com/ubuntu natty partner
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list.save:## developers who want to ship their latest software.
/etc/apt/sources.list.save:deb http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list.save:deb-src http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-proposed restricted main multiverse universe
/etc/apt/sources.list.save:deb http://archive.ubuntu.com/ubuntu quantal-backports restricted main multiverse universe
/etc/apt/sources.list.save:deb http://ppa.launchpad.net/sabily.team/ppa/ubuntu quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.save:deb-src http://ppa.launchpad.net/sabily.team/ppa/ubuntu quantal main # disabled on upgrade to quantal
grep: /etc/apt/trustdb.gpg: Permission denied
Binary file /etc/apt/trusted.gpg matches
Binary file /etc/apt/trusted.gpg~ matches
Binary file /etc/apt/trusted.gpg.d/wuala-keyring.gpg matches
Binary file /etc/apt/trusted.gpg.d/wuala-keyring.gpg~ matches

```

Thank you in advance very much
Ali Alushari

---

### Post by matt_symes on 2012-08-23
Hi

I'm not quite with you. What problems are you having ?

Kind regards

---

### Post by nicholasjohnoba on 2012-10-17
I have the same problem.

```

/etc/apt/apt.conf.d/20changelog:// Server information for apt-changelog
/etc/apt/apt.conf.d/20changelog:APT {
/etc/apt/apt.conf.d/20changelog:  Changelogs {
/etc/apt/apt.conf.d/20changelog:    Server "http://changelogs.ubuntu.com/changelogs";
/etc/apt/apt.conf.d/20changelog:  };
/etc/apt/apt.conf.d/20changelog:};
/etc/apt/apt.conf.d/50unattended-upgrades:// Automatically upgrade packages from these (origin:archive) pairs
/etc/apt/apt.conf.d/50unattended-upgrades:Unattended-Upgrade::Allowed-Origins {
/etc/apt/apt.conf.d/50unattended-upgrades:	"${distro_id}:${distro_codename}-security";
/etc/apt/apt.conf.d/50unattended-upgrades://	"${distro_id}:${distro_codename}-updates";
/etc/apt/apt.conf.d/50unattended-upgrades://	"${distro_id}:${distro_codename}-proposed";
/etc/apt/apt.conf.d/50unattended-upgrades://	"${distro_id}:${distro_codename}-backports";
/etc/apt/apt.conf.d/50unattended-upgrades:};
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// List of packages to not update
/etc/apt/apt.conf.d/50unattended-upgrades:Unattended-Upgrade::Package-Blacklist {
/etc/apt/apt.conf.d/50unattended-upgrades://	"vim";
/etc/apt/apt.conf.d/50unattended-upgrades://	"libc6";
/etc/apt/apt.conf.d/50unattended-upgrades://	"libc6-dev";
/etc/apt/apt.conf.d/50unattended-upgrades://	"libc6-i686";
/etc/apt/apt.conf.d/50unattended-upgrades:};
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// This option allows you to control if on a unclean dpkg exit
/etc/apt/apt.conf.d/50unattended-upgrades:// unattended-upgrades will automatically run 
/etc/apt/apt.conf.d/50unattended-upgrades://   dpkg --force-confold --configure -a
/etc/apt/apt.conf.d/50unattended-upgrades:// The default is true, to ensure updates keep getting installed
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::AutoFixInterruptedDpkg "false";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Split the upgrade into the smallest possible chunks so that
/etc/apt/apt.conf.d/50unattended-upgrades:// they can be interrupted with SIGUSR1. This makes the upgrade
/etc/apt/apt.conf.d/50unattended-upgrades:// a bit slower but it has the benefit that shutdown while a upgrade
/etc/apt/apt.conf.d/50unattended-upgrades:// is running is possible (with a small delay)
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::MinimalSteps "true";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Install all unattended-upgrades when the machine is shuting down
/etc/apt/apt.conf.d/50unattended-upgrades:// instead of doing it in the background while the machine is running
/etc/apt/apt.conf.d/50unattended-upgrades:// This will (obviously) make shutdown slower
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::InstallOnShutdown "true";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Send email to this address for problems or packages upgrades
/etc/apt/apt.conf.d/50unattended-upgrades:// If empty or unset then no email is sent, make sure that you
/etc/apt/apt.conf.d/50unattended-upgrades:// have a working mail setup on your system. A package that provides
/etc/apt/apt.conf.d/50unattended-upgrades:// 'mailx' must be installed. E.g. "user@example.com"
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::Mail "root";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Set this value to "true" to get emails only on errors. Default
/etc/apt/apt.conf.d/50unattended-upgrades:// is to always send a mail if Unattended-Upgrade::Mail is set
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::MailOnlyOnError "true";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Do automatic removal of new unused dependencies after the upgrade
/etc/apt/apt.conf.d/50unattended-upgrades:// (equivalent to apt-get autoremove)
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::Remove-Unused-Dependencies "false";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Automatically reboot *WITHOUT CONFIRMATION* if a 
/etc/apt/apt.conf.d/50unattended-upgrades:// the file /var/run/reboot-required is found after the upgrade 
/etc/apt/apt.conf.d/50unattended-upgrades://Unattended-Upgrade::Automatic-Reboot "false";
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:
/etc/apt/apt.conf.d/50unattended-upgrades:// Use apt bandwidth limit feature, this example limits the download
/etc/apt/apt.conf.d/50unattended-upgrades:// speed to 70kb/sec
/etc/apt/apt.conf.d/50unattended-upgrades://Acquire::http::Dl-Limit "70";
/etc/apt/apt.conf.d/00aptitude:Aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
/etc/apt/apt.conf.d/99synaptic:APT::Install-Recommends "true";
/etc/apt/apt.conf.d/00trustcdrom:APT::Authentication::TrustCDROM "true";
/etc/apt/apt.conf.d/20archive:APT::Archives::MaxAge "30";
/etc/apt/apt.conf.d/20archive:APT::Archives::MinAge "2";
/etc/apt/apt.conf.d/20archive:APT::Archives::MaxSize "500";
/etc/apt/apt.conf.d/15update-stamp:APT::Update::Post-Invoke-Success {"touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";};
/etc/apt/apt.conf.d/01autoremove:APT
/etc/apt/apt.conf.d/01autoremove:{
/etc/apt/apt.conf.d/01autoremove:  NeverAutoRemove
/etc/apt/apt.conf.d/01autoremove:  {
/etc/apt/apt.conf.d/01autoremove:	"^firmware-linux.*";
/etc/apt/apt.conf.d/01autoremove:	"^linux-firmware$";
/etc/apt/apt.conf.d/01autoremove:	"^linux-image.*";
/etc/apt/apt.conf.d/01autoremove:	"^kfreebsd-image.*";
/etc/apt/apt.conf.d/01autoremove:	"^linux-restricted-modules.*";
/etc/apt/apt.conf.d/01autoremove:	"^linux-ubuntu-modules-.*";
/etc/apt/apt.conf.d/01autoremove:	"^gnumach$";
/etc/apt/apt.conf.d/01autoremove:	"^gnumach-image.*";
/etc/apt/apt.conf.d/01autoremove:  };
/etc/apt/apt.conf.d/01autoremove:
/etc/apt/apt.conf.d/01autoremove:  Never-MarkAuto-Sections
/etc/apt/apt.conf.d/01autoremove:  {
/etc/apt/apt.conf.d/01autoremove:	"metapackages";
/etc/apt/apt.conf.d/01autoremove:	"restricted/metapackages";
/etc/apt/apt.conf.d/01autoremove:	"universe/metapackages";
/etc/apt/apt.conf.d/01autoremove:	"multiverse/metapackages";
/etc/apt/apt.conf.d/01autoremove:	"oldlibs";
/etc/apt/apt.conf.d/01autoremove:	"restricted/oldlibs";
/etc/apt/apt.conf.d/01autoremove:	"universe/oldlibs";
/etc/apt/apt.conf.d/01autoremove:	"multiverse/oldlibs";
/etc/apt/apt.conf.d/01autoremove:  };
/etc/apt/apt.conf.d/01autoremove:};
/etc/apt/apt.conf.d/20dbus:// Notify all clients to reload the cache
/etc/apt/apt.conf.d/20dbus:APT::Update::Post-Invoke-Success { "[ ! -f /var/run/dbus/system_bus_socket ] || /usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged || true"; };
/etc/apt/apt.conf.d/10periodic:APT::Periodic::Update-Package-Lists "1";
/etc/apt/apt.conf.d/10periodic:APT::Periodic::Download-Upgradeable-Packages "0";
/etc/apt/apt.conf.d/10periodic:APT::Periodic::AutocleanInterval "0";
/etc/apt/apt.conf.d/99update-notifier:DPkg::Post-Invoke {"if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi "; };
/etc/apt/apt.conf.d/70debconf:// Pre-configure all packages with debconf before they are installed.
/etc/apt/apt.conf.d/70debconf:// If you don't like it, comment it out.
/etc/apt/apt.conf.d/70debconf:DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Beta i386 (20120926)]/ quantal main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal main restricted
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal universe
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal universe
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-updates universe
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal multiverse
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal multiverse
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-security main restricted
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-security main restricted
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-security universe
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-security universe
/etc/apt/sources.list:deb http://ph.archive.ubuntu.com/ubuntu/ quantal-security multiverse
/etc/apt/sources.list:deb-src http://ph.archive.ubuntu.com/ubuntu/ quantal-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb http://archive.canonical.com/ubuntu quantal partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu quantal partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list:deb http://archive.canonical.com/ quantal partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ quantal partner
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list.d/moonlight-team-pinta-quantal.list.save:deb http://ppa.launchpad.net/moonlight-team/pinta/ubuntu quantal main
/etc/apt/sources.list.d/moonlight-team-pinta-quantal.list.save:deb-src http://ppa.launchpad.net/moonlight-team/pinta/ubuntu quantal main
/etc/apt/sources.list.d/moonlight-team-pinta-quantal.list:deb http://ppa.launchpad.net/moonlight-team/pinta/ubuntu quantal main
/etc/apt/sources.list.d/moonlight-team-pinta-quantal.list:deb-src http://ppa.launchpad.net/moonlight-team/pinta/ubuntu quantal main
/etc/apt/sources.list.d/tualatrix-ppa-quantal.list.save:deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
/etc/apt/sources.list.d/tualatrix-ppa-quantal.list.save:deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
/etc/apt/sources.list.d/folke-schwinning-personal-quantal.list.save:deb http://ppa.launchpad.net/folke-schwinning/personal/ubuntu quantal main
/etc/apt/sources.list.d/folke-schwinning-personal-quantal.list.save:deb-src http://ppa.launchpad.net/folke-schwinning/personal/ubuntu quantal main
/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main
/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list.save:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main
/etc/apt/sources.list.d/tualatrix-ppa-quantal.list:deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
/etc/apt/sources.list.d/tualatrix-ppa-quantal.list:deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu quantal main
/etc/apt/sources.list.d/folke-schwinning-personal-quantal.list:deb http://ppa.launchpad.net/folke-schwinning/personal/ubuntu quantal main
/etc/apt/sources.list.d/folke-schwinning-personal-quantal.list:deb-src http://ppa.launchpad.net/folke-schwinning/personal/ubuntu quantal main
/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main
/etc/apt/sources.list.d/ubuntu-wine-ppa-quantal.list:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu quantal main
/etc/apt/sources.list.save:# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Beta i386 (20120926)]/ quantal main restricted
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list.save:# newer versions of the distribution.
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal main restricted
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal main restricted
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list.save:## distribution.
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list.save:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list.save:## review or updates from the Ubuntu security team.
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal universe
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal universe
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-updates universe
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-updates universe
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list.save:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list.save:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list.save:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list.save:## security team.
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal multiverse
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal multiverse
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list.save:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list.save:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list.save:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list.save:## or updates from the Ubuntu security team.
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-security main restricted
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-security main restricted
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-security universe
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-security universe
/etc/apt/sources.list.save:deb http://mirror.siamdata.co.th/ubuntu/ quantal-security multiverse
/etc/apt/sources.list.save:deb-src http://mirror.siamdata.co.th/ubuntu/ quantal-security multiverse
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list.save:## 'partner' repository.
/etc/apt/sources.list.save:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list.save:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list.save:# deb http://archive.canonical.com/ubuntu quantal partner
/etc/apt/sources.list.save:# deb-src http://archive.canonical.com/ubuntu quantal partner
/etc/apt/sources.list.save:
/etc/apt/sources.list.save:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list.save:## developers who want to ship their latest software.
/etc/apt/sources.list.save:deb http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list.save:deb http://archive.canonical.com/ quantal partner
/etc/apt/sources.list.save:deb-src http://archive.canonical.com/ quantal partner
/etc/apt/sources.list.save:deb-src http://extras.ubuntu.com/ubuntu quantal main
grep: /etc/apt/trustdb.gpg: Permission denied
Binary file /etc/apt/trusted.gpg matches
Binary file /etc/apt/trusted.gpg~ matches

```

---


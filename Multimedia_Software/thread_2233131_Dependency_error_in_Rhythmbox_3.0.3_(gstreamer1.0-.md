---
title: "Dependency error in Rhythmbox 3.0.3 (gstreamer1.0-plugins-ugly (i386)"
date: 2014-07-06
forum: Multimedia Software
---

### Post by xtrailrunner on 2014-07-06
After upgrading Ubuntu to 14.04 I can't extract tracks from a CD anymore. I get a message that additional software is required to encode media and it tries to install gstreamer1.0-plugins-ugly (i386). This fails because of unmet dependencies:
The following packages have unmet dependencies:

gstreamer1.0-plugins-ugly:i386: Depends: libc6 (>= 2.7) but 2.19-0ubuntu6 is to be installed
                                Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed
                                Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
                                Depends: libglib2.0-0 (>= 2.37.3) but 2.40.0-2 is to be installed
                                Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed
                                Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is to be installed
libxine2-plugins: Depends: libxine2-ffmpeg (>= 1.2.4-2ubuntu1) but 1.2.4-2ubuntu1 is to be installed
                  Depends: libxine2-misc-plugins (>= 1.2.4-2ubuntu1) but 1.2.4-2ubuntu1 is to be installed

I have tried to reinstall rhythmbox but without any effect. Why it requires gstreamer1.0-plugins-ugly:i386 on a 64-bit system ?

---

### Post by ibjsb4 on 2014-07-06
Something weird going on here.  Please post the output of ..
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by xtrailrunner on 2014-07-07
Here it is

**(1)  cat /etc/apt/sources.list**

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe restricted multiverse main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe restricted multiverse main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe restricted multiverse main #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

## Virtualbox
deb [http://jbrout.free.fr/download/debian](http://jbrout.free.fr/download/debian) binary/
# deb-src [http://jbrout.free.fr/download/debian](http://jbrout.free.fr/download/debian) binary/

## Linux Mint
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) qiana main upstream import
[B]
(2)  ls /etc/apt/sources.list.d/*.list[/B]
/etc/apt/sources.list.d/bimsebasse-cinnamonextras-precise.list
/etc/apt/sources.list.d/bimsebasse-cinnamonextras-quantal.list
/etc/apt/sources.list.d/fossfreedom-rhythmbox-plugins-raring.list
/etc/apt/sources.list.d/fossfreedom-rhythmbox-trusty.list
/etc/apt/sources.list.d/google-webdesigner.list
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-nightly-saucy.list
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-quantal.list
/etc/apt/sources.list.d/kazam-team-unstable-series-quantal.list
/etc/apt/sources.list.d/langdalepl-gvfs-mtp-raring.list
/etc/apt/sources.list.d/libreoffice-ppa-precise.list
/etc/apt/sources.list.d/libreoffice-ppa-quantal.list
/etc/apt/sources.list.d/mc3man-trusty-media-trusty.list
/etc/apt/sources.list.d/mint.list
/etc/apt/sources.list.d/mozillateam-thunderbird-stable-precise.list
/etc/apt/sources.list.d/mozillateam-thunderbird-stable-quantal.list
/etc/apt/sources.list.d/nilarimogard-webupd8-raring.list
/etc/apt/sources.list.d/nvbn-rm-ppa-raring.list
/etc/apt/sources.list.d/pipelight-stable-saucy.list
/etc/apt/sources.list.d/rabbitvcs-ppa-precise.list
/etc/apt/sources.list.d/rabbitvcs-ppa-raring.list
/etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-quantal.list
/etc/apt/sources.list.d/rohityadav-vlmc-saucy.list
/etc/apt/sources.list.d/tobias-quinn-gsmz-raring.list
/etc/apt/sources.list.d/tualatrix-ppa-precise.list
/etc/apt/sources.list.d/tualatrix-ppa-quantal.list
/etc/apt/sources.list.d/virtualbox.list
/etc/apt/sources.list.d/virtualbox.org.list
/etc/apt/sources.list.d/webupd8team-java-precise.list
/etc/apt/sources.list.d/webupd8team-java-quantal.list
/etc/apt/sources.list.d/webupd8team-unstable-raring.list

---

### Post by ibjsb4 on 2014-07-07
You have old PPA's in sources.list.d, I would start there and remove them.  All you want to keep is 'trusty' ppa.  Open up your software sources ..

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

And while your there, uncheck 'source code'; unless you are building your own packages from source, you will not be using this option.  This will not help with your problem, but will speed up the update process.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Update and upgrade after this and see if the errors go away.

---

### Post by xtrailrunner on 2014-07-07
I have removed obsolete repositories, unchecked source code repos and updated the system but error remains.
What seems strange to me:
Rhythmbox demands to install gstreamer1.0-plugins-ugly:i386 but gstreamer1.0-plugins-ugly is already installed.
My system is 64bit.
Thanks !
Juergen

---

### Post by mc4man on 2014-07-07
Why don't you log into a guest session & try to rip/encode a track in Rb. If it works there then it's a local config to your user.

---

### Post by xtrailrunner on 2014-07-07
Good advice. With guest user MP3 extraction works.
Should I completely remove the RB config from my user ?

---

### Post by mc4man on 2014-07-07
> **xtrailrunner said:**
> 
Should I completely remove the RB config from my user ?
Yeah, whatever you can find concerning RB (which isn't much
Maybe also ~/.cache/gstreamer-1.0/<the bin file inside>

---

### Post by xtrailrunner on 2014-07-07
Solved:
I had to remove the files under <user>/.local/share/gstreamer-1.0/presets.
@mc4man
Thanks for your guidance.

---


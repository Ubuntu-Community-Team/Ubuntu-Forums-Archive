---
title: "[SOLVED] Xubuntu 7.10 dvd playback"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Chachee on 2007-12-16
Ok,
  I've done a ton of search, and I was able to set this up on my 6.06 workstation, but I can't seem to get DVD playback installed on my laptop.  I've tried with totem-gstreamer, and totem-xine.  When I installed I didn't have access to the internet so it's got a ton of stuff in my sources file.

  Here's some information - 

```
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
# Line commented out by installer because it failed to verify:
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
# Line commented out by installer because it failed to verify:
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse
# Line commented out by installer because it failed to verify:
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
  deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
  deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
  deb http://archive.canonical.com/ubuntu gutsy partner
  deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
  deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
  deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
  deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
  deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
  deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
  deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://packages.medibuntu.org/ gutsy free non-free

```

```
sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gnomevfs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I also walked through-
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

```
 sudo apt-get install xubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gnomevfs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Not really sure what to check or do at this point.  Seemed like 6.06 had much better walkthroughs.. maybe I'm just too dense.

Thanks for any help.

Jeremy

---

### Post by Chachee on 2007-12-16
As usual I realized the answer was still out there and finally found the 7.10 documentation.  I hate being the guy who didn't RTFM...

DVD's work now.  Wireless, Intel Graphic drivers, and compiz to go.

Tanks,

JT

---


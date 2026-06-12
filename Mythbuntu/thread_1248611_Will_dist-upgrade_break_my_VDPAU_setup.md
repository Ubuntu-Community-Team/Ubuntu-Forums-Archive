---
title: "Will dist-upgrade break my VDPAU setup?"
date: 2009-08-24
forum: Mythbuntu
---

### Post by bcg30506 on 2009-08-24
The motd is telling me there are upgrades available.  I've done this in the past and had a devil of a time getting my nvidia VDPAU drivers working again.  In the list today, I do not see the nvidia driver changing, but the kernel is.  So is this going to break my X setup?  Would I be better off leaving well enough alone?  Are there changes in here that would help fix bugs, like the tearing I get with the Temporal 2x deinterlacer?  Would it be safer or riskier to only do an apt-get upgrade instead of a dist-upgrade?

Lots of questions I know, but I'm just trying to get a handle on keeping up to date with the least amount of pain each time.

```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-restricted-modules-2.6.28-15-generic
The following packages will be upgraded:
  apache2-mpm-prefork apache2-utils apache2.2-common libcurl3 libcurl3-gnutls libgnutls26 libmyth-0.21-0 libmyth-perl libmyth-python linux-generic linux-headers-generic linux-image-generic linux-libc-dev
  linux-restricted-modules-common linux-restricted-modules-generic mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-frontend mythtv-transcode-utils xfce4-terminal
23 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 64.0MB of archives.
After this operation, 173MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

OR:

```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  apache2-mpm-prefork apache2-utils apache2.2-common libcurl3 libcurl3-gnutls libgnutls26 libmyth-0.21-0 libmyth-perl libmyth-python linux-libc-dev linux-restricted-modules-common mythtv mythtv-backend
  mythtv-backend-master mythtv-common mythtv-database mythtv-frontend mythtv-transcode-utils xfce4-terminal
19 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 29.1MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?

```

---

### Post by jyavenard on 2009-08-25
It depends which version of mythtv you're running and which repository you are using.

VDPAU isn't supported in 0.21-fixes, so if you're updating to a version from a repository which doesn't have the vdpau backport, then yes you will use your VDPAU

---

### Post by bcg30506 on 2009-08-25
Here is my sources.list:

```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://packages.medibuntu.org/ jaunty free non-free

deb http://ppa.launchpad.net/ripps818/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ripps818/ppa/ubuntu jaunty main

```

---

### Post by nickrout on 2009-08-26
Is there a problem with your current setup? 

If not, why change it?

---

### Post by bcg30506 on 2009-08-26
> **nickrout said:**
> Is there a problem with your current setup? 

If not, why change it?

I've been trying to stay up with the weekly releases as long as they aren't too major and seem stable.  Currently, most everything is working except for video tearing in scenes that pan when using VDPAU playback profile (and yes, Composite is disabled), and current conditions in mythweather are not updating.  I'm in no rush since it is primarily working, but thought some bug fixes may be available.

edit: I went ahead and did the dist-upgrade after adding avenard's repository to get the latest mythtv-vdpau builds with the beta nvidia 190 drivers.  It worked fine and my tearing issue is gone.

---

### Post by jyavenard on 2009-08-26
> **bcg30506 said:**
> Here is my sources.list:

```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://packages.medibuntu.org/ jaunty free non-free

deb http://ppa.launchpad.net/ripps818/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ripps818/ppa/ubuntu jaunty main

```

There's no VDPAU related packages here (VDPAU isn't supported in Ubuntu/MythBuntu 0.21 packages)

---

### Post by bcg30506 on 2009-08-26
> **bcg30506 said:**
> edit: I went ahead and did the dist-upgrade **after adding avenard's repository** to get the latest mythtv-vdpau builds with the beta nvidia 190 drivers.  It worked fine and my tearing issue is gone.

Yes, but I added your's first and then did the upgrade.

```
deb http://www.avenard.org/files/ubuntu-repos jaunty release testing
```

---


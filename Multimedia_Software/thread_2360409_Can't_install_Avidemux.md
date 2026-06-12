---
title: "Can't install Avidemux"
date: 2017-05-04
forum: Multimedia Software
---

### Post by Gingalone on 2017-05-04
I have a Ubuntu 16.04 AMD 64 system on a Samsung 5 Ultrabook and it is working pretty well.
But, when I tried to install avidemux, I got troubles! I tried installing the package from the official Avidemux site (avidemux-qt_2.5.4-0ubuntu16_amd64) with Ubuntu Software but the installation sticks; then I tried installing a ppa (getdeb-repository_0.1-1~getdeb1_all.deb) then install with Synaptic, but got a final error message from synaptic: 
```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:91
```
I also tried several forums but with no avail!
Thank you for any help!

---

### Post by howefield on 2017-05-04
So what does the sources.list look like ?

Can you post the output of... 

```
cat /etc/apt/sources.list
```

---

### Post by Gingalone on 2017-05-08
Thank you for reply howefield; here the answer to the suggested command: ```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://it.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://it.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial universe
deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

---

### Post by howefield on 2017-05-08
OK, try commenting out line 91.

From a terminal use the command..

```
sudo apt edit-sources
```

Select option 2 (nano) and scroll down to the 6th from bottom line.. the one that looks like

```
deb http://archive.canonical.com/ubuntu xenial partner
```

and place a # sign at the beginning of that line.

Ctrl + o, press enter and then Ctrl + x to save and exit the file. Then you can try 

```
sudo apt update
```

if you get further errors then post hem back here.

---

### Post by Gingalone on 2017-05-09
Thank you howefield, I did that and then the installation of Avidemux with Synaptic completed without errors. BUT, alas, Avidemux does not work. 
In the command bar there are two instances of it:  
"Avidemux 2.6 (GTK)" and "Avidemux 2.6 (Jobs Qt 4)" both of them not working: an icon with a question mark appears for a few second on the Unity launcher and then disappears (same behaviour for the two commands)...

---

### Post by howefield on 2017-05-09
> **Gingalone said:**
> Thank you howefield, I did that and then the installation of Avidemux with Synaptic completed without errors. BUT, alas, Avidemux does not work. 

Try opening via a terminal, if there are errors you will be more likely to get an idea of what is preventing it from working.

> In the command bar there are two instances of it: "Avidemux 2.6 (GTK)" and "Avidemux 2.6 (Jobs Qt 4)" both of them not working: an icon with a question mark appears for a few second on the Unity launcher and then disappears (same behaviour for the two commands)...

Not sure what you mean by "command bar" but if you have two versions of Avidemux installed, might be best to purge them and try again.

What is the output of..

```
apt-cache policy avidemux*
```

---

### Post by Gingalone on 2017-05-09
> Try opening via a terminal, if there are errors you will be more likely to get an idea of what is preventing it from working.
 ```
avidemux
avidemux: error while loading shared libraries: libADM6avcodec.so.56: cannot open shared object file: No such file or directory

```> Not sure what you mean by "command bar" but if you have two versions of Avidemux installed, might be best to purge them and try again.
I mean the Unity dash> What is the output of..
```
apt-cache policy avidemux*
```
Here we go (very long response!):```
apt-cache policy avidemux*
avidemux2.6-unstable-plugins-qt4:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-qt5:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-qt:
  Installed: (none)
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
     1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
avidemux2.6-unstable-jobs-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-jobs-dbg:
  Installed: (none)
  Candidate: (none)
  Version table:
avidemux2.6-plugins-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-vsproxy-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-jobs-dbg:
  Installed: (none)
  Candidate: (none)
  Version table:
avidemux2.6-unstable-cli:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-common:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-vsproxy-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-common:
  Installed: 1:2.6.20-1~getdeb1
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
 *** 1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
        100 /var/lib/dpkg/status
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-vsproxy-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-gtk:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux-plugins:
  Installed: (none)
  Candidate: (none)
  Version table:
avidemux2.6-unstable-plugins-gtk-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-jobs-qt4:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-jobs-qt5:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-vsproxy-qt4:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-vsproxy-qt5:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-jobs-qt4:
  Installed: 1:2.6.18-1~ppa+xenial1
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
 *** 1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
avidemux2.6-jobs-qt5:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-qt4:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-qt5:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-vsproxy-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-cli-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-jobs-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-cli:
  Installed: (none)
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
     1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-qt:
  Installed: (none)
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
     1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
avidemux-common:
  Installed: (none)
  Candidate: (none)
  Version table:
avidemux2.6-unstable-plugins-vsproxy:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-jobs:
  Installed: (none)
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
     1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
avidemux2.6-plugins-gtk-dbg:
  Installed: (none)
  Candidate: 1:2.6.12-2~ppa+xenial7
  Version table:
     1:2.6.12-2~ppa+xenial7 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-gtk:
  Installed: 1:2.6.12-2~ppa+xenial7
  Candidate: 1:2.6.12-2~ppa+xenial7
  Version table:
 *** 1:2.6.12-2~ppa+xenial7 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
avidemux2.6-plugins-settings:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-jobs:
  Installed: (none)
  Candidate: (none)
  Version table:
avidemux2.6-gtk-dbg:
  Installed: (none)
  Candidate: 1:2.6.12-2~ppa+xenial7
  Version table:
     1:2.6.12-2~ppa+xenial7 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-jobs-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-cli:
  Installed: (none)
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
     1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-gtk-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-common:
  Installed: 1:2.6.20-1~getdeb1
  Candidate: 1:2.6.20-1~getdeb1
  Version table:
 *** 1:2.6.20-1~getdeb1 500
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps amd64 Packages
        500 http://archive.getdeb.net/ubuntu xenial-getdeb/apps i386 Packages
        100 /var/lib/dpkg/status
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main i386 Packages
     1:2.6.12-2~ppa+xenial7 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main i386 Packages
avidemux2.6-unstable-plugins-vsproxy-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-common:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main i386 Packages
     1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main i386 Packages
avidemux2.6-plugins-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux:
  Installed: (none)
  Candidate: (none)
  Version table:
avidemux2.6-unstable-plugins-settings:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-cli-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-common-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-gtk:
  Installed: 1:2.6.12-2~ppa+xenial7
  Candidate: 1:2.6.12-2~ppa+xenial7
  Version table:
 *** 1:2.6.12-2~ppa+xenial7 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
avidemux2.6-plugins-vsproxy-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-cli-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-qt4-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-vsproxy-qt4:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-vsproxy-qt5:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-cli:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-cli-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-qt4:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-qt5:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-gtk:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.05.03-20.58.20-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-common-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-unstable-plugins-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0
  Version table:
     1:2.6.12+git2016.10.24-08.30.08-1~ppa+xenial0 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-qt4:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-qt5:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
avidemux2.6-plugins-vsproxy:
  Installed: 1:2.6.18-1~ppa+xenial1
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
 *** 1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
avidemux2.6-jobs-qt5-dbg:
  Installed: (none)
  Candidate: 1:2.6.18-1~ppa+xenial1
  Version table:
     1:2.6.18-1~ppa+xenial1 500
        500 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial/main amd64 Packages
``` thank you for help!

---

### Post by mc4man on 2017-05-09
you are using a ppa, - [https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial](https://launchpad.net/~rebuntu16/+archive/ubuntu/avidemux+unofficial) + you have getdeb plus apparently you tried to install the 2.5.4-0ubuntu16 package which is for 15.10, not 16.04
The ppa & getdeb are offering 2.6.x which are far as the missing plugin would be libADM6avcodec.so.57 not libADM6avcodec.so.56 which I guess was used in 2.5.4

You best bet would be to remove any & all instances of avidemux & installed plugins & then just use either the ppa or getdeb.

What's this show?
```
which avidemux
```
If it returns /usr/bin/avidemux then run & post 
```
file /usr/bin/avidemux
```

---

### Post by Gingalone on 2017-05-10
Thank you mc4man (even if I get a bit "cryptic" your suggestions);)
```
which avidemux
/usr/bin/avidemux

file /usr/bin/avidemux
/usr/bin/avidemux: symbolic link to /etc/alternatives/avidemux
```

---

### Post by mc4man on 2017-05-11
> **Gingalone said:**
> Thank you mc4man (even if I get a bit "cryptic" your suggestions);)
```
which avidemux
/usr/bin/avidemux

file /usr/bin/avidemux
/usr/bin/avidemux: symbolic link to /etc/alternatives/avidemux
```

so one last time will show whether using the 2.5.4 version (avidemux[COLOR="#FF0000"]2[/COLOR]) or the 2.6.x version (avidemux[COLOR="#FF0000"]3[/COLOR]
```
file /etc/alternatives/avidemux
```

Also of interest - 
```
sudo update-alternatives --config avidemux
```

---

### Post by Gingalone on 2017-05-16
Thank you and sorry for delay...

> so one last time will show whether using the 2.5.4 version (avidemux2) or the 2.6.x version (avidemux3)
```
Code:
file /etc/alternatives/avidemux
/etc/alternatives/avidemux: symbolic link to /usr/bin/avidemux3_gtk

```
Also of interest -
```
Code:
sudo update-alternatives --config avidemux
[sudo] password for gigius: 
There is only one alternative in link group avidemux (providing /usr/bin/avidemux): /usr/bin/avidemux3_gtk
Nothing to configure.

```

---

### Post by Gingalone on 2017-06-05
mc4man said:
> You best bet would be to remove any & all instances of avidemux & installed plugins & then just use either the ppa or getdeb.
I did as you said mc4man, sticking to the getdeb source.
Now Avidemux works but I still have two alternatives (it looks...) in the dash: Avidemux 2.6 (Jobs) and Avidemux 2.6 (Qt) and only the second works. 
What is Avidemux Jobs?
Thank you

---

### Post by mc4man on 2017-06-05
Search avidemux Jobs,  maybe it'll be informative 
(- seems to be an external app to open/load a job queue, whether you'll use or whether it'll ever work who knows...

---


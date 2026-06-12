---
title: "gstreamer0.10-plugins-ugly     problem"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by adg69 on 2008-02-25
I am trying to get mp3's etc to play and thus need to install the above package, but when I try to install it it refuses too, stating that there is a "conflict with other installed packages" and I need to use synaptic package manager to resolve the problem.

Okay the problem is, what I am looking for, the error doesn't tell me what package is causing the conflict, and thus what I need to remove, so how do I find what is causing the conflict?

I am running Ubuntu 7.10

---

### Post by deepclutch on 2008-02-25
..may be coz of u using a 3rd party repo?
always do "sudo apt-get update && sudo apt-get upgrade" when INTERNET is ON.
anyways,no problemo,u can install it as follows:
open a terminal(in menu Applications>Accsrs>terminal)
do:
```
sudo dpkg -i **--force-overwrite**  /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb
```
and/or
```

sudo dpkg -i  **--force-overwrite**   /var/cache/apt/archives/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb

```
I found below 2 packages in my Ubuntu 7.10:
 > ll /mnt/var/cache/apt/archives/ |grep gstreamer0.10-plugins-ugly*
-rw-r--r-- 1 root root   236290 2007-08-31 19:33 gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb
-rw-r--r-- 1 root root    41588 2007-06-21 05:33 gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb


---

### Post by adg69 on 2008-02-25
tried your advice and got the following error messages


andrew@andrew-desktop:~$ sudo dpkg -i --force-overwrite  /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb

[sudo] password for andrew:

dpkg: error processing /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb


andrew@andrew-desktop:~$ sudo dpkg -i  --force-overwrite   /var/cache/apt/archives/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb
dpkg: error processing /var/cache/apt/archives/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb


any clues ?

---

### Post by deepclutch on 2008-02-25
^that means u dont have those .debs in ur download directory!:p
below thing holds true for ur case:
> **always do "sudo apt-get update && sudo apt-get upgrade" when INTERNET is ON.**
anyways,below is the .debs which u have to download to ur Desktop and have to install via dpkg --force-overwrite -i .deb option.

[http://mirrors.kernel.org/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb)

and:
[http://mirrors.kernel.org/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb)
^download it,go to the directory where u downloaded .debs and install it!

So,My advice to you is,to check ur /etc/apt/sources.list be similar to mine:
if some repo are missing,add that.make sure u remove **"#"** in front of main repositories.

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free

# Seveas&#8217; packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl gutsy-seveas all
# deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

deb http://ppa.launchpad.net/mozillateam/ubuntu gutsy main


```

---

### Post by adg69 on 2008-02-25
When I try to install this package 

[http://mirrors.kernel.org/ubuntu/poo...untu2_i386.deb](http://mirrors.kernel.org/ubuntu/poo...untu2_i386.deb)

I get error, dependency file missing "libid3tag0"


get same error, different file name for second package "liblame0"





new too linux so I am not sure the exact process for checking source list etc???

---

### Post by deepclutch on 2008-02-25
^if u choose to install all these packages manually,u have to download each dependencies as shown earlier.
my advice is to u edit /etc/apt/sources.list as mine and launch System>admin>Synaptic manager ;then press "reload" button when INTERNET IS CONNECTED!.
Then do a  "sudo apt-get install -f"

---

### Post by adg69 on 2008-02-25
Okay I have sorted this out now I went here [http://packages.ubuntu.com/gutsy/libid3tag0](http://packages.ubuntu.com/gutsy/libid3tag0) and got the packages I required to get this working. Thanks for your help.

---


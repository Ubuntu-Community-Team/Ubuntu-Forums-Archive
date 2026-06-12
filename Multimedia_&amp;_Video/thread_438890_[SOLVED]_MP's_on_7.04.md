---
title: "[SOLVED] MP's on 7.04?"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by waggygee on 2007-05-10
Today, I reformatted my 20gb harddrive and installed Ubuntu 7.04 Feisty Fawn (i had previously run Ubuntu 6.06)..... The 7.04 seems very nice but leaves me annoyed with setting up my media player to play mp3 music files. How do I do it?

---

### Post by renzokuken on 2007-05-10
use automatix to install all the necessary codecs

[www.getautomatix.com](www.getautomatix.com)

---

### Post by reclusivemonkey on 2007-05-10
You don't need to install Automatix just to play mp3's. Just clicking on an mp3 file in the file browser should prompt you to install the necessary codecs. There has been a lot of work done in Feisty to make this process easier.

---

### Post by waggygee on 2007-05-10
Upon trying to download codecs using default Ubuntu software, I receive this in a windows that pops up as it finishes:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Using Automix I receive this:

An apt-based error has occured and installation was unsuccessfull

and on another window this comes up:

An error occured
The following details are provided:
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by reclusivemonkey on 2007-05-10
Do you have a working internet connection?

---

### Post by waggygee on 2007-05-10
Yes... It downloads everything about half way then cuts then off. (Surfing the web works perfectly)

---

### Post by reclusivemonkey on 2007-05-10
It could be the repos are suffering excessive load. Can you attach your /etc/apt/sources.list?

---

### Post by waggygee on 2007-05-10
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

Is this the correct one?

---

### Post by reclusivemonkey on 2007-05-10
Yep thats the one. There doesn't look to be anything out of the ordinary. However I did notice this on your repo, and the gb one which I use here in the UK;

[http://gb.archive.ubuntu.com/ubuntu/Archive-Update-in-Progress-prat.ubuntu.com](http://gb.archive.ubuntu.com/ubuntu/Archive-Update-in-Progress-prat.ubuntu.com) dated today. I would try again tomorrow and see if you get the same results.

---


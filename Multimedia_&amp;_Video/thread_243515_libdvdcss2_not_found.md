---
title: "libdvdcss2 not found"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by TDave on 2006-08-25
All,

Just done a fresh Kubuntu install on a formerly dead machine and added universe and multiverse respositories as I've done previusly.

Upon trying to obtain the extra codecs however, and dvd playback capability, it comes up with problems for various things (most importantly libdvdcss2 - the usual 'No Installation Candidate story.
libdvdread3 does work fine though.

I am stumped as to what it could be as my sources.list looks as I think it should look...

```

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

```

Any help or advice on where to find a .deb would be greatly appreciated.
As mentioned, it also leaves me unable to install a few of the other codecs, although libxine-extracodecs installed without issue.

Cheers

---

### Post by tkjacobsen on 2006-08-25
run the following script to install libdvdcss:

/usr/share/doc/libdvdread3/examples/install-css.sh

It is not in the Ubuntu repositories.. However you can find it in the seveas repo: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl)
Direct link from seveas: [http://mirror.ubuntulinux.nl/pool/dapper-seveas/extras/libdvdcss2_1.2.9-0.0ubuntu2_i386.deb](http://mirror.ubuntulinux.nl/pool/dapper-seveas/extras/libdvdcss2_1.2.9-0.0ubuntu2_i386.deb)

---

### Post by TDave on 2006-08-25
Excellent

Muchos gracias

---


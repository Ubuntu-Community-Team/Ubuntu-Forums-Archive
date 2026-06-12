---
title: "MPlayer install errors"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by hannahb on 2007-04-27
trying to install mplayer this is what i get 

hannahb@laptop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
           Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
           Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
           Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
           Depends: libdvdread3 (>= 0.9.6) but 0.9.4-5.1 is to be installed
           Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.3 is to be installed
           Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
           Depends: libggi2 (>= 1:2.2.1) but it is not going to be installed
           Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
           Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
           Depends: liblame0 (>= 3.96.1) but it is not going to be installed
           Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed
           Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
           Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages

I am new to this linux thing.All i want to do is play wmv files. If there is an eaiser way to do this please advise.
Thanks 
Brian

---

### Post by hannahb on 2007-04-27
mplayer install errors 

--------------------------------------------------------------------------------

trying to install mplayer this is what i get 

hannahb@laptop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mplayer: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
Depends: libdvdread3 (>= 0.9.6) but 0.9.4-5.1 is to be installed
Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.3 is to be installed
Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
Depends: libggi2 (>= 1:2.2.1) but it is not going to be installed
Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
Depends: liblame0 (>= 3.96.1) but it is not going to be installed
Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed
Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages

I am new to this linux thing.All i want to do is play wmv files. If there is an eaiser way to do this please advise.
Thanks 
Brian

---

### Post by taurus on 2007-04-27
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by hannahb on 2007-04-27
yep here it is

annahb@laptop:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse

---

### Post by guill3 on 2008-02-04
Hi ev1 (its me first post here)

sorry for the bump, but could you solve the problem ? Same here!

---


---
title: "Mythtv Radeon 9800 all in wonder pro installation"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by d1sturbanc3 on 2006-09-17
Hi, I'm trying to my TV tuner to work. I have an all in wonder radeon 9800 pro. I'm currently running KDE as my desktop environment. I just migrated my desktop from gentoo to ubuntu.

First of all, what driver do I need? I have installed GATOS which supports all in wonder.

but here is what I get when I try installing mythtv

```

root@ubuntu:/home/yan# apt-get install mythtv
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
  mythtv: Depends: mythtv-frontend (= 0.17-3) but it is not going to be installed
          Depends: mythtv-backend (= 0.17-3) but it is not going to be installed
E: Broken packages

```

Thank you
I tried apt-get install all the dependency, but it eventually unmerged my KDE-core. Are there more specific documentation/HOWTO's?

---

### Post by d1sturbanc3 on 2006-09-17
Oh here is my source list

```


deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe multiverse
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse

```

I'm guessing it's my source list

---

### Post by watson540 on 2006-11-10
MythTV is not compatible with your card, you'll be lucky enough to get a clear picture (let alone sound) with avview or xawtv. Buy a hardware based tv card . ATI sucks
(coming from a proud owner of a radeon 9800 aiw ) I have jacked with this tv capability for two years now, my only hope would be to somehow get vmware to recognize my real card and then let me view tv from within xp inside vmware (pipe dream?)

---


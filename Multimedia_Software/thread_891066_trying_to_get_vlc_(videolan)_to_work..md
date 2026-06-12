---
title: "trying to get vlc (videolan) to work."
date: 2008-08-15
forum: Multimedia Software
---

### Post by markmorgan on 2008-08-15
Hello

New laptop - took xp off and installed ubuntu via dvd - internet connection working and upgraded OS to 8.04

trying to get videolan to install - followed instructions to the letter but keep getting this error (see below)

any help would be appreciated - im trying to find any program that will play at least some of my videos !

thanks 

mark

root@football:~# sudo apt-get install vlc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  vlc: Depends: libtar but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not installable
       Depends: libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1) but it is not going to be installed
       Depends: libwxbase2.6-0 (>= 2.6.3.2.2) but it is not installable
       Depends: libwxgtk2.6-0 (>= 2.6.3.2.2) but it is not installable
       Depends: libxosd2 (>= 2.2.13) but it is not installable
       Depends: vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Broken packages
root@football:~#

---

### Post by jualin on 2008-08-15
Go to the terminal and post the output of > cat /etc/apt/sources.list

---

### Post by markmorgan on 2008-08-15
sure - here you go. :confused:

deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ
erse multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted
universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security univer

---

### Post by shirilover on 2008-08-16
That first line appears to be a problem.
Also, you don't seem to have the following:

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

---

### Post by jualin on 2008-08-16
> **markmorgan said:**
> sure - here you go. :confused:



Don't get confused :), the file that you showed us was the repositories sources, which is pretty much where Ubuntu is going to download the applications from. I agree with shirilover, you need to add the multiverse repositories. You can do it his way if you want to do it via terminal or via the GUI using Synaptic Package Manager. Just open Synaptic Package Manager found under System, Administration. Then select Settings, Repositories, and check the one that says "Software restricted by copyright or legal issues(Multiverse)". Then reload the repositories and try installing VLC again.

---

### Post by markmorgan on 2008-08-16
Thank you both. I will give this a try

Mark

---

### Post by markmorgan on 2008-08-16
Worked like a charm - thanks once again :)

M

---

### Post by jualin on 2008-08-16
Glad it worked. Greetings from Miami, FL!

---

### Post by headie on 2008-10-04
> **jualin said:**
> Glad it worked. Greetings from Miami, FL!

Thanx guys for making Ubuntu the better OS.

---


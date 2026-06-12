---
title: "unmet dependencies with mythtv"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by bjdekruif on 2007-06-25
Hello all, 

I am trying to install the backend/frontend installation of MythTV with Ubuntu server 6.10.
I use the guide from [https://help.ubuntu.com/community/MythTV_Edgy](https://help.ubuntu.com/community/MythTV_Edgy) and
the first steps  go well, but when I try to install mythtv, I get unmet dependencies.

So, when I try:

sudo apt-get install mythtv-frontend gdm ubuntu-artwork xterm openbox gnome-screensaver xserver-xorg gsfonts-x11 xfonts-100dpi xfonts-75dpi msttcorefonts xfonts-base mysql-server mythtv-backend mythtv-database usplash-theme-ubuntu 

I get:

The following packages have unmet dependencies:
  mythtv-backend: Depends: mythtv-common (= 0.20-svn20070122-0.0ubuntu6~edgy1) but 0.20-0.2ubuntu2 is to be installed
  mythtv-frontend: Depends: mythtv-common (= 0.20-svn20070122-0.0ubuntu6~edgy1) but 0.20-0.2ubuntu2 is to be installed
E: Broken packages

I tried to first install mythtv-common, but this does not resolve the problem.
Does anyone know how I get MythTV to work?
Should I update to 7.04, or won't that resolve anything?

I am running an AMD64, might it be of influence for this problem.

Thanks

bas

---

### Post by tgm4883 on 2007-06-25
AMD64 shouldn't be the problem, I run 64-bit (although Feisty) on my mythtv box.  Have you tried Feisty on the box yet?  Some things are much easier to setup. 

Also, why did you do a server install?

---

### Post by bjdekruif on 2007-06-25
Thanks for your quick reply. 

I am downloading Feisty right now, so that will be the next thing I try. However, I am afraid that I get the same error (always be optimistic ;-)

I installed the server mainly because this gave me a very minimal installation. As I only want to use the computer as MythBox, I don't need all kind of games and other stuff on it. 
Do you imagine that the server installation will be part of the problem?

bas

---

### Post by tgm4883 on 2007-06-25
Did some checking and the backend and frontend in the edgy repos are .20-0.2ubuntu2.  Can you post your sources.list

---

### Post by tgm4883 on 2007-06-25
Not sure if the server is giving your problems.  If you try the feisty server cd, follow the guide to the letter, and still have problems then I guess the server cd is giving you problems.  As I know the feisty guide works for 64-bit.  But lets see your sources.list first.

---

### Post by tgm4883 on 2007-06-25
Almost forgot, per the guide, if you install the alternate cd and follow the guide you wont get the extra stuff you dont need, as the guide has you install a command line system first.

---

### Post by bjdekruif on 2007-06-25
Hello, 

I added the four lines at the bottom of the sources.list, 
for the rest it is the default file.

sources.list
# 
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#manually added
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

---

### Post by tgm4883 on 2007-06-25
Did you run sudo apt-get update after you added those lines?

---

### Post by bjdekruif on 2007-06-25
jep,

First an apt-get update, then an apt-get upgrade

This worked ok, although I saw a kernel-image was held back

---

### Post by tgm4883 on 2007-06-25
The problem seems to be that mythtv-common isn't in edgy-backports, although we are not sure why as it should be.  If you want to use edgy, then wait as were looking into why it's not there.  If you want to use feisty, things should work as normal and follow the guide

---

### Post by bjdekruif on 2007-06-25
Thanks for all your time!

I just started to install Feisty, and it seems to be working fine.
Everything just out of the box

Thanks again

---


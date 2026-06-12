---
title: "Nvidia Profiler replacing Nvidia Cuda Toolkit for Ubuntu 14.04?"
date: 2014-04-07
forum: Multimedia Software
---

### Post by javierdl on 2014-04-07
The following terminal feedback I obtained it while running a "test" of Ubuntu 14.04 from a USB driver. Prior to attempting to install Cuda I successfully switched to the Nvidia 331 driver.

> ubuntu@ubuntu:~$ sudo apt-get install nvidia-cuda-toolkit
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package nvidia-cuda-toolkit is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
nvidia-profiler


E: Package 'nvidia-cuda-toolkit' has no installation candidate

Can anyone confirm if indeed I should be installing the Nvidia Profiler instead?

JDL

---

### Post by 23dornot23d on 2014-04-07
Is that the 32 bit 14.04 system by any chance .......... as I came across that same message ......

It worked ok for me in the 64 bit 14.04 system though .........

Whats the results of these commands in a terminal

[B]lsb_release -a

uname -a [/B]

---

### Post by javierdl on 2014-04-07
Hey 23dornot23d!
Glad you asked. "trusty-desktop-amd64" is the ISO file name.
I'll have to load the USB drive with the Ubuntu trusty to try your commands. I'll get back later or tomorrow.

JDL

---

### Post by 23dornot23d on 2014-04-07
Ok 64 bit is ok ........ that is what I used the other day ...... the commands will confirm that ......
and also tell us which kernel is running ( just so we know .... )

The only other thing then is to check we have the same sources.list

Will put mine here ...... the only thing I have done to it was to change it to a uk server for speed ......

but its in /etc/apt/sources.list

if you spot any differences between your own and mine let me know what they are please or post your own and
I will have a look through.

```

# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Alpha amd64 (20140314)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

---

### Post by javierdl on 2014-04-08
> ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.13.0-23-generic #45-Ubuntu SMP Fri Apr 4 06:58:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Now, about creating that Sources list, I have no idea how you made it. How am I to create it?

---

### Post by javierdl on 2014-04-08
Today I tried to install the Nvidia Profiler into the Livedrive with Ubuntu 14.04. But I got the following errors:

> dpkg: error processing package rarian-compat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 docbook-xml
 rarian-compat

> Nvidia Profiler failed, see below feedback from terminal:
E: docbook-xml: package is in a very bad inconsistent state; you should  reinstall it before attempting configuration
E: rarian-compat: dependency problems - leaving unconfigured


Package docbook-xml is not configured yet.


dpkg: error processing package rarian-compat (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-profiler (5.0.35-7ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package docbook-xml (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of rarian-compat:
 rarian-compat depends on docbook-xml; however:
  Package docbook-xml is not configured yet.


It seems it's not compatible with Trusty, is this right?

Btw, I also attempted to install Nvidia Nsight, but I also got some errors:

> Nvidia nsight failed, see below feedback from terminal:
Processing triggers for ca-certificates (20130906ubuntu2) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
done.
done.
Errors were encountered while processing:
 docbook-xml
 rarian-compat
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package docbook-xml (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of rarian-compat:
 rarian-compat depends on docbook-xml; however:
  Package docbook-xml is not configured yet.


> dpkg: error processing package rarian-compat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 docbook-xml
 rarian-compat


E: docbook-xml: package is in a very bad inconsistent state; you should  reinstall it before attempting configuration
E: rarian-compat: dependency problems - leaving unconfigured


Only compatible with rarian maybe?

Aside of this, I did manage to install Blender 2.70 in Trusty. But Cuda is not showing in the User Prefs yet :(

---

### Post by 23dornot23d on 2014-04-08
Have you done this since installing it .........  

**sudo apt-get update**

maybe the package lists are not uptodate yet ........



or go into synaptic package manager and have a look for the cuda files as that updates as you go into it

see if the **nvidia-cuda-toolkit** is showing in the search ..........

I got everything running and its doing nicely now ........ have done my first animation with it .......

[IMG]http://i.minus.com/iPTTcQLaWTUiX.gif[/IMG]

Got to do something with the eyes though and the beak ;)

---


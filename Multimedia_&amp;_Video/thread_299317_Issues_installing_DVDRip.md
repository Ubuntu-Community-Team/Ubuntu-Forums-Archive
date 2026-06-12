---
title: "Issues installing DVD::Rip"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by Sutur on 2006-11-13
[B]Running Edgy Edge on a 32 bit kernel using AMD 64 X2.

Having problems installing dvd::rip. I looked around for answers but couldn't find much of any use. Does anyone know what the problem is from the report given by apt-get below?[/B]

[COLOR="RoyalBlue"][I]sutur@Muspell:~$ sudo apt-get install dvdrip
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

The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not going to be installed
          Depends: libgtk-pixbuf-perl but it is not installable
E: Broken packages
sutur@Muspell:~$ [/I][/COLOR]

**What must I do to find the appropriate packages that are *not* broken, if that is actually the case here?**

---

### Post by Sutur on 2006-11-15
Bump for help.

---

### Post by Sutur on 2006-11-16
Bump for help.

---

### Post by Hobbes on 2006-11-16
I just installed it, no errors, warnings, or other troublesome messages...

What repositories do you have enabled (either in synaptic or /etc/apt/sources.list), my guess would be that you need to enable the multiverse repository, which has transcode in it.

---

### Post by Sutur on 2006-11-16
**Hobbies, thank you for the help. I believe I have indeed enabled multiverse and universe repositories as Synaptic tells me there are approx. 20,000 packages to choose from including multi and universe ones. But in case I'm missing something silly, here is my sources.list**

[COLOR="RoyalBlue"][I]deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse[/I][/COLOR]

**I also took the liberty of trying ad additional sudo apt-get update then repeating the original command, but received the same error about dependencies not being available.**

---

### Post by SlCKB0Y on 2006-11-17
> **Sutur said:**
> **Hobbies, thank you for the help. I believe I have indeed enabled multiverse and universe repositories as Synaptic tells me there are approx. 20,000 packages to choose from including multi and universe ones. But in case I'm missing something silly, here is my sources.list**

[COLOR="RoyalBlue"][I]deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse[/I][/COLOR]

**I also took the liberty of trying ad additional sudo apt-get update then repeating the original command, but received the same error about dependencies not being available.**

Dude, you have the DAPPER multiverse enabled. What are you doing?
:confused:

If things are stuffing up in a major way you are lucky.

Change those lines to edgy, then do an apt-get update and an apt-get dist-upgrade

---

### Post by Sutur on 2006-11-17
...Doh...](*,)

---

### Post by Krash1201 on 2006-11-19
i am having a problem with dvd::rip but not the one posted here.  I am using edgy on a machine upgrade, with all of its problems through update manager, from dapper.  dvd::rip worked fine in dapper.  after the upgrade it stopped working, so i uninstalled it and reinstalled it.  during the install i get the following error:

```
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1.8.0-0.1_i386.deb
 /var/cache/apt/archives/libanyevent-perl_1.02-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?  thanks in advance.

---


---
title: "unable to install jackd on newly installed lucid lynx"
date: 2010-05-03
forum: Multimedia Software
---

### Post by nowave7 on 2010-05-03
Just installed Lucid Lynx on a clean system, and tried to install ubuntu-studio, but failed due to inability to install jackd. The specific message is:

```
The following packages have unmet dependencies:
  jackd: Depends: libjack0 (= 0.116.1-4ubuntu2) but it is not going to be installed
         Recommends: qjackctl but it is not going to be installed
```

The funny thing is that the library in question is present on the system, and according to apt it is at the latest version. Any ideas as to what is happening?

---

### Post by P4man on 2010-05-03
weird. On my system I also have a 0.118 svn version, not sure what pulled that in (or if its there by default). The dependency you quoted seems to require an older one and its "=" rather than ">=". 

That said, I dont feel like installing ubuntu studio, but when I run apt-get install ubuntustudio-desktop it doesnt complain. It lists all packages it will install  and asks my okay. Does it only happen after you downloaded it all?

---

### Post by nowave7 on 2010-05-03
Well, I first spotted this when trying to install ubuntu studio, but upon further investigation it seems that the problem is with jackd. So it's not strictly related to ubuntu studio.

A bit of an off topic. Noticed **a lot** of dependency problems in lucid lynx, for instance was unable to install vim, since newer version of vim-common was installed, and solved this after downgrading the vim-common, strange problems installing open office (), as well as binutils(2.20.1-3ubuntu5) and binutils-dev (available version 2.20-4ubuntu3). This is all done on a fresh system, with only the following repositories added:
```
http://archive.canonical.com/ubuntu lucid partner
```
Apologize for the off-topic, but had to express my dissatisfaction with the new LTS.

---

### Post by mc4man on 2010-05-03
> jackd: Depends: libjack0 (= 0.116.1-4ubuntu2)
That is the karmic version

The binutils deal

 > binutils (2.20.1-3ubuntu5) lucid; urgency=low

  * Rebuild statically linked ld.static binary against recent libc.

 -- Matthias Klose <doko@ubuntu.com>  Sun, 18 Apr 2010 23:50:53 +0200

[COLOR="Blue"]binutils (2.20.1-3ubuntu4) lucid; urgency=low[/COLOR]

  * Apply patch for PR gas/11456: Use memcpy to copy overlap memory.

 -- Matthias Klose <doko@ubuntu.com>  Wed, [COLOR="Blue"]31 Mar[/COLOR] 2010 19:10:39 +0200

Have you updated since you installed? and what/when did you install lucid from

Are all the lucid software sources enabled?
(main, universe, restricted, multiverse, plus source code

---

### Post by nowave7 on 2010-05-03
Downloaded yesterday from the official Ubuntu site.
```
#uname -a
Linux acer-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```
and from the CD:
DISKNAME  Ubuntu 10.04 LTS "Lucid Lynx" - Release i386
I assume this is not some alpha/beta release.
And this is the content of the /etc/apt/sources.list file
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://rs.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://rs.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://rs.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid universe
deb http://rs.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://rs.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://rs.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://rs.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://rs.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```
I haven't done any updates, but that shouldn't be the problem, AFAIK.

---

### Post by mc4man on 2010-05-03
Well that looks fine - out of curiosity if you search libjack in synaptic what version is either installed or available?

same for jackd
(for the heck of it first  run a 
```
sudo apt-get update
```

Is your binutils-dev up to the current version? (2.20.1-3ubuntu5

---

### Post by nowave7 on 2010-05-03
Well, libjack0 is at 0.118+svn3796-1ubuntu2, which is the latest version reported by synaptic, while jackd is at 0.116.1-4ubuntu2. Which seems to be the cause of the problem. Did an apt-get update before looking for versions.

For the binutils-dev part, installed version is the same as the latest version, which is 2.20.1-3ubuntu5. One thing I noticed, and is a bit strange, is that when I opened up the properties for the binutils package, and checked the versions tab, there were two available versions, the one currently installed, which was tagged by (now), and 2.20-4ubuntu3, which was tagged by (lucid), and this is the version available for binutils-dev. Hope this shed some light...

P.S. checked versions tab for libjack as well, same thing there... :(

---

### Post by mc4man on 2010-05-03
Weird on the jackd (where the karmic version is coming from...?

what if you go here, download and try to install the proper jackd

[http://packages.ubuntu.com/lucid/jackd](http://packages.ubuntu.com/lucid/jackd)

What does synaptic show for jackd-firewire
[http://packages.ubuntu.com/lucid/jackd-firewire](http://packages.ubuntu.com/lucid/jackd-firewire)

If you wish to try to manually install both do jackd first

(am going to boot up to the release live cd (just dl'ed) to see what jackd is available

This is what you should show for qjackctl
[http://packages.ubuntu.com/lucid/qjackctl](http://packages.ubuntu.com/lucid/qjackctl)

---

### Post by nowave7 on 2010-05-03
This is what shows when trying to install jackd manually through gdebi

```
Error: Breaks existing package 'libjack0' conflict: jackd (> 0.118+svn3796-1ubuntu2)
```
While qjackctl is at version 0.3.4-0ubuntu2, which doesn't seem to be right 0.3.4-0ubuntu4. And I couldn't even find jackd-firewire through synaptic?!

I'm guessing a new fresh install is in place (which I thought this was)?

---

### Post by mc4man on 2010-05-03
> Error: Breaks existing package 'libjack0' conflict: jackd (> 0.118+svn3796-1ubuntu2)

See the same on the live cd (so forget the dl'ed package
Can't quite see what the issue is there
But..
> ubuntu@ubuntu:~$ sudo apt-get install jackd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  jackd-firewire libaudio2 libffado2 libmng1 libqt4-xml libqtcore4 libqtgui4
  libxml++2.6-2 qjackctl
.....ect. 
Setting up jackd (0.118+svn3796-1ubuntu2) ...

And it installs fine 

Of some interest
If I install jackd as above and then go to /var/cache/archives and try to re-install the jackd that was just installed I get the same message as from trying to install the downloaded one (what a bit of a screw up

So - you're going to need to install jackd from either apt-get or synaptic - obviously it has to show the current lucid version

---

### Post by mc4man on 2010-05-03
Try this instead - 
take your downloaded jackd, put it in a folder, cd to that folder and run 
```
sudo dpkg -i *.deb
```

Should work
If you want to then  dl the firewire.. and qjack..  and also put in a folder ( do jackd first by itself

> ubuntu@ubuntu:~/Downloads$ sudo dpkg -i *.deb
Selecting previously deselected package jackd.
(Reading database ... 129907 files and directories currently installed.)
Unpacking jackd (from jackd_0.118+svn3796-1ubuntu2_i386.deb) ...
Setting up jackd (0.118+svn3796-1ubuntu2) ...

Processing triggers for man-db ...


---

### Post by nowave7 on 2010-05-04
Okay, will try it as soon as I get back home, not at my laptop right now. Thanks for the help. I'll report on how it went.

---

### Post by mc4man on 2010-05-04
Well good luck
Just to clarify something 

It appears that only the jackd package will fail with gdebi, why I'm still not sure.

So after using dpkg on it as described you could try going back to synaptic or apt-get to complete installing what you wanted (ubuntustudio or ubuntu-studio-audio ..?

IF any of the other packages are wrong versioned for some reason then your can try manually dl'ing and installing - I'd use gdebi for that initially - less chance or broken packages, use dpkg if 2 or more need to be installed at the same time

I'm fairly confident you can work this out, though where the karmic versions came from remains a mystery

---

### Post by nowave7 on 2010-05-04
Hey mc4man,

Found out what the problem was. As it turned out, I selected the repositories hosted in the country I'm coming from (Serbia), and it appears that the hosted packages are not the freshest ones. Anyway, to cut the long story short, I've chosen the US repositories and everything is ok now. Will mark this thread as solved. Thanks for the help!

---


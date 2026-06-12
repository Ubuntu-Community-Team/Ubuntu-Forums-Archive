---
title: "Problems with installing gstreamer."
date: 2010-04-12
forum: Multimedia Software
---

### Post by Totally-Lemonified on 2010-04-12
I tried to install gstreamer through Rhythmbox but only got a "Fix broken packages first" error message.  I tried to fix the broken packages in the Synaptic Package Manager but it said there were none to be fixed.  I tried to install the gstreamer stuff from Synaptic Package Manager and got this message 

> gstreamer0.10-ffmpeg:
 Depends: libavcodec52 (>=3:0.svn20090303-1) but it is not installable or
     libavcodec-extra-52 but it is not going to be installed
 Depends: libavformat52 (>=3:0.svn20090303-1) but it is not installable or
     libavformat-extra-52 but it is not going to be installedI then tried to install libavformat-extra-52 and got this message 

> libavcodec-extra-52:
 Depends: libgsm1 (>=1.0.13) but it is not installable
 Depends: libschroedinger-1.0-0 (>=1.0.0) but it is not installableI couldn't find either of the packages contained in the last message.  I appreciate any help offered!

---

### Post by mikewhatever on 2010-04-12
geit /etc/apt/sources.list

Can you post your sources list.

---

### Post by WinterRain on 2010-04-12
> **mikewhatever said:**
> **geit** /etc/apt/sources.list

Can you post your sources list.
Do:
```
cat /etc/apt/sources.list
```

---

### Post by Totally-Lemonified on 2010-04-12
Cheers again, I'm really quite new so all help is useful.

```
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by mikewhatever on 2010-04-12
Can you run the following from a terminal and post the output:

sudo apt-get update

I suspect some of the sources are not accessible.

---

### Post by Totally-Lemonified on 2010-04-12
I can't see any issues,

```
Hit http://gb.archive.ubuntu.com karmic Release.gpg
Hit http://gb.archive.ubuntu.com karmic/main Translation-en_GB
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com karmic Release
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com karmic-security Release
Hit http://gb.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/main Packages        
Hit http://gb.archive.ubuntu.com karmic/main Packages
Hit http://gb.archive.ubuntu.com karmic/restricted Packages
Hit http://gb.archive.ubuntu.com karmic/main Sources
Hit http://gb.archive.ubuntu.com karmic/restricted Sources
Hit http://gb.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://gb.archive.ubuntu.com karmic/universe Sources
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
```

---

### Post by WinterRain on 2010-04-12
> **Totally-Lemonified said:**
> Cheers again, I'm really quite new so all help is useful.

```
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B]# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner[/B]

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```
> **mikewhatever said:**
> 
I suspect some of the sources are not accessible.
Yeah, the partner repos are disabled.

I bolded the lines where you should remove the "#" from the beginning of both lines.
Then
```
sudo apt-get update
```
Or you could just go to system>administration>software sources, open the "other software" tab and check off the partner line.

To edit your sources list, do:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by wojox on 2010-04-12
Just need medibuntu and non-free-codecs: [http://wojox.homelinux.net/?p=77](http://wojox.homelinux.net/?p=77)

---

### Post by Totally-Lemonified on 2010-04-12
> **WinterRain said:**
> Yeah, the partner repos are disabled.

I bolded the lines where you should remove the "#" from the beginning of both lines.
Then
```
sudo apt-get update
```Or you could just go to system>administration>software sources, open the "other software" tab and check off the partner line.

To edit your sources list, do:
```
gksudo gedit /etc/apt/sources.list
```

Thanks for the help!  Unfortunately it didn't do a whole lot.  I tried removing the hashes from the 'backport' repository as well but it didn't do anything either.

---

### Post by WinterRain on 2010-04-12
I just re-read your original post, and may have missed this myself, but it seems you have broken packages. Try:
```
sudo apt-get install -f
```

---

### Post by mikewhatever on 2010-04-12
> **WinterRain said:**
> Yeah, the partner repos are disabled.


So? Neither gstreamer0.10-ffmpeg, nor libavcodec52 is in partner repository.

---

### Post by Totally-Lemonified on 2010-04-12
> **WinterRain said:**
> I just re-read your original post, and may have missed this myself, but it seems you have broken packages. Try:
```
sudo apt-get install -f
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

No problems there.

---

### Post by WinterRain on 2010-04-12
> **mikewhatever said:**
> So? Neither gstreamer0.10-ffmpeg, nor libavcodec52 is in partner repository.

Excuse me, I'm human. (and make mistakes) I want to help this person as much as you do.

---

### Post by Totally-Lemonified on 2010-04-13
> **wojox said:**
> Just need medibuntu and non-free-codecs: [http://wojox.homelinux.net/?p=77](http://wojox.homelinux.net/?p=77)

I also tried this as a way of just avoiding the problem altogether but it's still not working.  This is such a pain!

---

### Post by Totally-Lemonified on 2010-04-13
Here's some extra information from the package manager that will hopefully help.

[IMG]http://imgur.com/sHbTJ.png[/IMG]


[IMG]http://imgur.com/yjooZ.png[/IMG]


[IMG]http://imgur.com/7cv8V.png[/IMG]


[IMG]http://imgur.com/7k3kx.png[/IMG]


[IMG]http://imgur.com/DHFYD.png[/IMG]

---

### Post by mikewhatever on 2010-04-13
> **WinterRain said:**
> Excuse me, I'm human. (and make mistakes) I want to help this person as much as you do.

Human, you say? And I thought you were a little green alien.:P

---

### Post by no2498 on 2010-04-13
look in the add/remove
gstreamer

see what is installed


on this computer 804 i can not get lib52


1 more thing if trying to play mp4's

install smplayer it loads the 264 codes
type it in a terminal tells you how to install it

hope this helps

---

### Post by mc4man on 2010-04-13
Something does seem to be amiss, asuming you are connected to the internet and have a karmic install - which it appears you do.

Run these in a terminal and see what happens

```
sudo apt-get update && sudo apt-get upgrade
```

If that does what it wants to do successfully then 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

If still no good post terminal output (though may be nothing new..

---

### Post by lidex on 2010-04-13
Try this page - it has all the info in one place:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Totally-Lemonified on 2010-04-14
Just want to say a massive thanks to everyone who was helping out but I just decided to go for a fresh install and everything seems to be working fine.  Thanks again!

---


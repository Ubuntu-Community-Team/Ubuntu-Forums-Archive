---
title: "Error on sudo apt-get update/upgrade"
date: 2010-06-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by miniCruzer on 2010-06-28
I'm running Ubuntu 10.10 Maverick Meerkat. Recently I tried running an update, and I get the following error with both **sudo apt-get update** and **sudo aptitude dist-upgrade**. I've pasted the output of **sudo apt-get update** and my sources.list, along with other commands that might help shed light on the situation.

```

sam@insanity:~$ sudo apt-get update
Get:1 http://archive.canonical.com maverick Release.gpg [189B]
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Get:2 http://ppa.launchpad.net lucid Release.gpg [307B]              
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ lucid/main Translation-en_US       
Get:3 http://archive.ubuntu.com maverick Release.gpg [189B]                                
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                           
Get:4 http://archive.canonical.com maverick Release [8,212B]         
Get:5 http://ppa.launchpad.net lucid Release [57.3kB]                                              
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Get:6 http://archive.ubuntu.com maverick-updates Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.canonical.com maverick Release                      
Err http://ppa.launchpad.net lucid Release                                                   
  
Get:7 http://archive.ubuntu.com maverick-security Release.gpg [189B]                         
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://archive.canonical.com maverick/partner Packages           
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Get:8 http://archive.ubuntu.com maverick Release [57.3kB]            
Err http://archive.ubuntu.com maverick Release                               
  
Hit http://archive.canonical.com maverick/partner Sources              
Hit http://archive.ubuntu.com maverick-updates Release               
Hit http://archive.ubuntu.com maverick-security Release              
Ign http://archive.ubuntu.com maverick-updates Release               
Ign http://archive.ubuntu.com maverick-security Release              
Hit http://archive.ubuntu.com maverick-updates/main Packages         
Hit http://archive.ubuntu.com maverick-updates/restricted Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/universe Packages
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main Packages
Hit http://archive.ubuntu.com maverick-security/restricted Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Packages
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Packages
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Get:9 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US
Get:10 http://dl.google.com stable Release [2,544B]
Err http://dl.google.com stable Release
  
Fetched 3,799B in 3s (1,064B/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com maverick Release: Unknown error executing gpgv
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com maverick Release: Unknown error executing gpgv

W: GPG error: http://archive.ubuntu.com maverick-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-security Release: Unknown error executing gpgv
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://dl.google.com stable Release: Unknown error executing gpgv

W: Failed to fetch http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/lucid/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
sam@insanity:~$ 

```
```


sam@insanity:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://archive.ubuntu.com/ubuntu/ maverick universe
deb http://archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://archive.ubuntu.com/ubuntu/ maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu/ maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu/ maverick-security universe
deb http://archive.ubuntu.com/ubuntu/ maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ maverick-security multiverse

```

```


sam@insanity:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  ffmpeg libavdevice52 libavfilter1 
The following NEW packages will be installed:
  libva1{a} 
The following packages will be upgraded:
  libavcodec-extra-52 libavformat-extra-52 libavutil-extra-50 libpostproc-extra-51 libswscale-extra-0 
5 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6,137kB of archives. After unpacking 106kB will be used.
The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (<= 4:0.6~svn20100505-99) but it is not installable or
                   libavcodec-extra-52 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
          Depends: libavformat52 (<= 4:0.6~svn20100505-99) but it is not installable or
                   libavformat-extra-52 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
          Depends: libavutil50 (<= 4:0.6~svn20100505-99) but it is not installable or
                   libavutil-extra-50 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
          Depends: libpostproc51 (<= 4:0.6~svn20100505-99) but it is not installable or
                   libpostproc-extra-51 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
          Depends: libswscale0 (<= 4:0.6~svn20100505-99) but it is not installable or
                   libswscale-extra-0 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
  libavfilter1: Depends: libavcodec52 (<= 4:0.6~svn20100505-99) but it is not installable or
                         libavcodec-extra-52 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
                Depends: libavutil50 (<= 4:0.6~svn20100505-99) but it is not installable or
                         libavutil-extra-50 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
                Depends: libswscale0 (<= 4:0.6~svn20100505-99) but it is not installable or
                         libswscale-extra-0 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
  libavdevice52: Depends: libavcodec52 (<= 4:0.6~svn20100505-99) but it is not installable or
                          libavcodec-extra-52 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
                 Depends: libavformat52 (<= 4:0.6~svn20100505-99) but it is not installable or
                          libavformat-extra-52 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
                 Depends: libavutil50 (<= 4:0.6~svn20100505-99) but it is not installable or
                          libavutil-extra-50 (<= 4:0.6~svn20100505-99) but 4:0.6-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libavcodec-extra-52 [4:0.6~svn20100505-1ubuntu5 (now)]
libavformat-extra-52 [4:0.6~svn20100505-1ubuntu5 (now)]
libavutil-extra-50 [4:0.6~svn20100505-1ubuntu5 (now)]
libpostproc-extra-51 [4:0.6~svn20100505-1ubuntu5 (now)]
libswscale-extra-0 [4:0.6~svn20100505-1ubuntu5 (now)]

Score is 100

Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
localepurge: checking for existence of /var/cache/localepurge...
localepurge: checking for existence of /var/cache/localepurge/localelist...
localepurge: checking system for new locale ...
localepurge: processing locale files ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: processing man pages ...
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: processing Gnome files ...
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: processing Omf files ...
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: processing KDE files ...
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

sam@insanity:~$ 

```

```


sam@insanity:~$ dpkg -l | grep gpgv
ii  gpgv                                              1.4.10-2ubuntu2                                 GNU privacy guard - signature verification t

```

---

### Post by lisati on 2010-06-29
Thread moved: Ubuntu 10.10 Maverick Meerkat is still in a pre-release form.

---

### Post by paul_in_london on 2010-06-29
Instead of: 

```
sudo aptitude **dist**-upgrade
```

try using:

```
sudo aptitude **safe**-upgrade
```

until the dependencies sort themselves out.

Look at the sticky as well re. "partial upgrades".

---

### Post by FakeOutdoorsman on 2010-06-29
Maybe you have a third-party repository or PPA that is interfering with your upgrade process.  Looks like *libavcodec52 4:0.6~svn20100505-99* may be from the Debian Experimental repository, or one of the third-party repositories is utilizing this, but I may be wrong.  Check the */etc/apt/sources.list.d/* directory for these troublesome repositories, move or delete them, run *sudo apt-get update*, and then try upgrading.

---

### Post by miniCruzer on 2010-06-29
> **paul_in_london said:**
> Instead of: 

```
sudo aptitude **dist**-upgrade
```

try using:

```
sudo aptitude **safe**-upgrade
```

until the dependencies sort themselves out.

Look at the sticky as well re. "partial upgrades".

No change after running this, thanks anyway.

[quote=FakeOutdoorsman]
Maybe you have a third-party repository or PPA that is interfering with your upgrade process. Looks like libavcodec52 4:0.6~svn20100505-99 may be from the Debian Experimental repository, or one of the third-party repositories is utilizing this, but I may be wrong. Check the /etc/apt/sources.list.d/ directory for these troublesome repositories, move or delete them, run sudo apt-get update, and then try upgrading.
[/quote]

I removed some Opera (Internet Browser) repositories, and ran update again, and there was no change. This is all that is in this directory:
```

sam@insanity:/etc/apt/sources.list.d$ ls
chromium-daily-ppa-lucid.list  google-chrome.list.distUpgrade
google-chrome.list             google-chrome.list.save

```

I do use Chromium, but not Google Chrome. Noting that Chromium and Google Chrome are so alike, I'm hesitant to remove google-chrome.*

Just to see what would happen if I removed everything from sources.list.d/ mv'd everything out temporarily, and tried update again, returning:
```


sam@insanity:/etc/apt/sources.list.d$ sudo apt-get update
Get:1 http://archive.canonical.com maverick Release.gpg [189B]
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Get:2 http://archive.canonical.com maverick Release [8,212B]
Ign http://archive.canonical.com maverick Release      
Get:3 http://archive.ubuntu.com maverick Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Hit http://archive.canonical.com maverick/partner Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com maverick-updates Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://archive.canonical.com maverick/partner Sources
Get:5 http://archive.ubuntu.com maverick-security Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Get:6 http://archive.ubuntu.com maverick Release [57.3kB]
Hit http://archive.ubuntu.com maverick-updates Release
Err http://archive.ubuntu.com maverick Release
  
Ign http://archive.ubuntu.com maverick-updates Release
Hit http://archive.ubuntu.com maverick-security Release
Ign http://archive.ubuntu.com maverick-security Release
Hit http://archive.ubuntu.com maverick-updates/main Packages
Hit http://archive.ubuntu.com maverick-updates/restricted Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/universe Packages
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main Packages
Hit http://archive.ubuntu.com maverick-security/restricted Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Packages
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Packages
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Fetched 758B in 1s (497B/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com maverick Release: Unknown error executing gpgv
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com maverick Release: Unknown error executing gpgv

W: GPG error: http://archive.ubuntu.com maverick-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-security Release: Unknown error executing gpgv
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
sam@insanity:/etc/apt/sources.list.d$ 

```

I appreciate the help.

---

### Post by dino99 on 2010-06-29
everything seems ok , dont worry about canonical partner as this is empty right now (only lucid)

---

### Post by FakeOutdoorsman on 2010-06-29
I believe removing the third-party repositories will resolve the libav* issues, but you still have the GPG errors.  I'm not sure what is causing this.  Perhaps the time on your machine is way off?  See [Strange error in Debian 4.0: error executing gpgv](http://johnny.chadda.se/article/strange-error-in-debian-40-error-executing-gpgv/).

---

### Post by mc4man on 2010-06-29
I would try updating ffmpeg and libs from synaptic - the initial packages in maverick were 4:0.6~svn20100505-1ubuntu[COLOR="Blue"]X[/COLOR] - the last of that series was 5
[https://launchpad.net/ubuntu/+source/ffmpeg-extra/4:0.6~svn20100505-1ubuntu5](https://launchpad.net/ubuntu/+source/ffmpeg-extra/4:0.6~svn20100505-1ubuntu5)

The recent rebuild(s) was to  4:0.6-1ubuntu[COLOR="Blue"]X[/COLOR]

---


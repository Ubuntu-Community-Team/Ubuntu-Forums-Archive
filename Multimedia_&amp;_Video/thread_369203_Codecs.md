---
title: "Codecs"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by Del Piero on 2007-02-24
Hi i am a noob, i just learned how to mount my drives few hours ago so take it easy :). Anyway i downloaded easybuntu and installed the ATI drivers through'it (need to confirm that they are installed but no idea). Anyway i installed everything in the codecs parts but still totem cant play any videos because of missing plugins, anyway i tried to install again and again (codecs alone this time) but no chance. and i got this error twice

> W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


please help :)

---

### Post by bapoumba on 2007-02-24
Hello,
you need to add Medibuntu repositories gpg key. Open a terminal (> Accessories > Terminal) and run:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```
[http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php")

Then:
```
sudo aptitude update
```

---

### Post by Del Piero on 2007-02-24
Thanks man the first error is gone but now when i open easybuntu and install the codecs, the download complete and everything then an error appear saying ''could not install fix broken packages first''.

---

### Post by bapoumba on 2007-02-24
You're welcome.
Please post the exact error message, which package is broken ?
What is the output to **sudo aptitude update** ?

---

### Post by Del Piero on 2007-02-24
> **bapoumba said:**
> You're welcome.
Please post the exact error message, which package is broken ?
What is the output to **sudo aptitude update** ?

sudo aptitude update
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg [191B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources [880B]
Get:6 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources [886B]
Fetched 1770B in 4s (411B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache


> Could not apply changes!
Fix broken packages first.

:confused:

---

### Post by bapoumba on 2007-02-24
Two bugs that look related to your problem:
[https://bugs.launchpad.net/easyubuntu/+bug/55353]("https://bugs.launchpad.net/easyubuntu/+bug/55353")
[https://bugs.launchpad.net/easyubuntu/+bug/47789]("https://bugs.launchpad.net/easyubuntu/+bug/47789")

Is this an issue with totem-gstreamer?
Try to install packages one by one, and see which one is causing trouble.

---

### Post by Del Piero on 2007-02-24
> **bapoumba said:**
> Two bugs that look related to your problem:
[https://bugs.launchpad.net/easyubuntu/+bug/55353]("https://bugs.launchpad.net/easyubuntu/+bug/55353")
[https://bugs.launchpad.net/easyubuntu/+bug/47789]("https://bugs.launchpad.net/easyubuntu/+bug/47789")

Is this an issue with totem-gstreamer?
Try to install packages one by one, and see which one is causing trouble.

I am clueless now whenever i try to install any package it downloads then this appears and nothing happens and nothing is installed:

[IMG]http://img160.imageshack.us/img160/8108/screenshotip1.png[/IMG]

---

### Post by bapoumba on 2007-02-24
could you post the output to **cat /etc/apt/sources.list** ?

---

### Post by Del Piero on 2007-02-24
> **bapoumba said:**
> could you post the output to **cat /etc/apt/sources.list** ?

there, btw thanks for doing this...

> omar@ubuntu:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

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
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



---

### Post by bapoumba on 2007-02-24
> **Del Piero said:**
> there, btw thanks for doing this...
No problem ;)

You will have to work a little on your source.list file. You have to enable universe and multiverse repositories.

1- Open a terminal, and run **sudo nano -B /etc/apt/sources.list**. nano is a small text editor that runs from a terminal. -B option will make a backup copy of your file with ~ extension.

2- Then you will have to [COLOR="Red"]remove[/COLOR] what is highlighted in red and [COLOR="SeaGreen"]add[/COLOR] what is in green:
```

# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
[COLOR="Red"]deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted[/COLOR]

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]#[/COLOR] deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe [COLOR="SeaGreen"]multiverse[/COLOR]
[COLOR="Red"]#[/COLOR] deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe [COLOR="SeaGreen"]multiverse[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
[COLOR="Red"]#[/COLOR] deb http://security.ubuntu.com/ubuntu dapper-security universe [COLOR="SeaGreen"]multiverse[/COLOR]
[COLOR="Red"]#[/COLOR] deb-src http://security.ubuntu.com/ubuntu dapper-security universe [COLOR="SeaGreen"]multiverse[/COLOR]
```

I mean, one line with cdrom to remove (it's in duplicate), 4 **#** to remove (these prevent the repositories to be taken into account) and 4 **multiverse** to add (on the proper lines, to enable multiverse repositories).

3- CTRL-O (like in ocean) to save the file, with the same name (hit <enter>)
4- CTRL-X to exit
5- **sudo aptitude update**
6- run easyubuntu again (I cannot walk you into easyubuntu, as I have never used it), but you should be okay. If easyubuntu does not work, we can help you install codecs the good old fashion way ;)

---

### Post by Del Piero on 2007-02-24
> **bapoumba said:**
> No problem ;)

You will have to work a little on your source.list file. You have to enable universe and multiverse repositories.

1- Open a terminal, and run **sudo nano -B /etc/apt/sources.list**. nano is a small text editor that runs from a terminal. -B option will make a backup copy of your file with ~ extension.

2- Then you will have to [COLOR="Red"]remove[/COLOR] what is highlighted in red and [COLOR="SeaGreen"]add[/COLOR] what is in green:
```

# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
[COLOR="Red"]deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted[/COLOR]

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]#[/COLOR] deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe [COLOR="SeaGreen"]multiverse[/COLOR]
[COLOR="Red"]#[/COLOR] deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe [COLOR="SeaGreen"]multiverse[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
[COLOR="Red"]#[/COLOR] deb http://security.ubuntu.com/ubuntu dapper-security universe [COLOR="SeaGreen"]multiverse[/COLOR]
[COLOR="Red"]#[/COLOR] deb-src http://security.ubuntu.com/ubuntu dapper-security universe [COLOR="SeaGreen"]multiverse[/COLOR]
```

I mean, one line with cdrom to remove (it's in duplicate), 4 **#** to remove (these prevent the repositories to be taken into account) and 4 **multiverse** to add (on the proper lines, to enable multiverse repositories).

3- CTRL-O (like in ocean) to save the file, with the same name (hit <enter>)
4- CTRL-X to exit
5- **sudo aptitude update**
6- run easyubuntu again (I cannot walk you into easyubuntu, as I have never used it), but you should be okay. If easyubuntu does not work, we can help you install codecs the good old fashion way ;)

My system failed, the swap partition changed its location on the hdd after i booted into windows, everything got messed and i had to delete, format, repartition, reinstall winxp, reinstall ubuntu. And guess what? i still have the same problem with easybuntu..that stupid white screen that i posted above and nothing happens. I guess i will go with the old fashion codecs installation please :) btw thanks again.

Anyway i am trying your method as we speak...

here is the output:

> omar@Ubuntuserv:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper Release.gpg
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper Release
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/main Packages
Ign cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/restricted Packages
Err cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:3 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [52.0kB]
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper/restricted Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper/restricted Sources
Get:6 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:7 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release [4425B]
Get:8 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages [2261B]
Get:9 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages [1671B]
Get:10 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources [880B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [4080B]
Get:12 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources [886B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6566B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [771B]
Get:15 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper/universe Sources [975kB]
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3507kB in 1m27s (40.0kB/s)
Reading package lists... Done


Just got this new errror with this message box:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
> cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by RRS on 2007-02-24
Go back to your sources list and add a comment ( # ) to the lines at the beginning with cdrom, that should eliminate the error message.

---

### Post by Del Piero on 2007-02-25
Finally i easybuntu installed the package, but when i play a video (divx movie) or any other type even the Ubuntu Nelson Mandela video it plays really slow and lags alot and drops alot of frames, from the looks of it it looks like display driver problem although easybuntu installed the ati drivers. I have a radeon 9200SE btw.

---

### Post by bapoumba on 2007-02-25
> **Del Piero said:**
> Finally i easybuntu installed the package, but when i play a video (divx movie) or any other type even the Ubuntu Nelson Mandela video it plays really slow and lags alot and drops alot of frames, from the looks of it it looks like display driver problem although easybuntu installed the ati drivers. I have a radeon 9200SE btw.
Congratulations!
I do not know much about video... You may want to start another thread, with this specific question.

---


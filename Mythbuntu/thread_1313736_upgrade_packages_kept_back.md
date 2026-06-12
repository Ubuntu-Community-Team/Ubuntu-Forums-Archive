---
title: "upgrade packages kept back"
date: 2009-11-04
forum: Mythbuntu
---

### Post by ZedThou on 2009-11-04
I'm new to the Debian package management system, and wondered what this meant. Today an apt-get upgrade produces this


```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mythtv-backend mythtv-frontend mythtv-transcode-utils
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

Is this anything to be concerned about?

---

### Post by sgunther on 2009-11-04
Did you first update;
$ sudo apt-get update

Then;
$ sudo apt-get upgrade

---

### Post by joshoekstra on 2009-11-04
Better not force partial upgrades, it just means that not all dependencies can be installed and so no package will be. As soon as al dependencies have been build they'll be available.
It seems to go a bit slower, probably because of heavy loads just after a new release....

---

### Post by ZedThou on 2009-11-05
I always update before upgrade. This has been going on for most of the day, how do I find out what the problem is?

```

$ apt-get -V upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
   mythtv-backend (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythtv-frontend (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythtv-transcode-utils (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
The following packages will be upgraded:
   binutils (2.20-0ubuntu1 => 2.20-0ubuntu2)
   libmyth-0.22-0 (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mytharchive (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythbrowser (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythflix (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythgallery (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythgame (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythmovies (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythmusic (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythnews (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythvideo (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   mythweather (0.22.0+fixes22705-0ubuntu0+mythbuntu3 => 0.22.0+fixes22722-0ubuntu0+mythbuntu3)
   nvidia-common (0.2.15 => 0.2.15.1)
   python (2.6.4~rc1-0ubuntu1 => 2.6.4-0ubuntu1)
   python-minimal (2.6.4~rc1-0ubuntu1 => 2.6.4-0ubuntu1)
   xsplash (0.8.4-0ubuntu1 => 0.8.5-0ubuntu1)
16 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 15.8MB of archives.
After this operation, 4,096B disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by ZedThou on 2009-12-04
Hate to bring up an old topic but I wonder if I have something misconfigured. For the last two weeks or so I have been unable to perform a complete upgrade. I do an update first, then on upgrade get this. Is it a problem with the ppa, or is the problem on my end?

```

$ sudo apt-get -V upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
   libmyth-0.22-0 (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   linux-generic (2.6.31.14.27 => 2.6.31.15.28)
   linux-headers-generic (2.6.31.14.27 => 2.6.31.15.28)
   linux-image-generic (2.6.31.14.27 => 2.6.31.15.28)
   mythbrowser (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythflix (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythgallery (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythgame (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythmovies (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythmusic (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythnews (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-backend (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-frontend (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-transcode-utils (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythvideo (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythweather (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
The following packages will be upgraded:
   libmyth-perl (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   libmyth-python (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mytharchive (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mytharchive-data (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-backend-master (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-common (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-database (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-blootube-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-blueosd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-graphite (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-iulius-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-metallurgy (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-mono-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-mythbuntu (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-projectgrayhem-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-retro-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-titivillus-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-themes (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythweb (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   nvidia-185-modaliases (185.18.36-0ubuntu9 => 185.18.36-0ubuntu9+ppa2)
21 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 43.7MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by tgm4883 on 2009-12-04
> **ZedThou said:**
> Hate to bring up an old topic but I wonder if I have something misconfigured. For the last two weeks or so I have been unable to perform a complete upgrade. I do an update first, then on upgrade get this. Is it a problem with the ppa, or is the problem on my end?

```

$ sudo apt-get -V upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
   libmyth-0.22-0 (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   linux-generic (2.6.31.14.27 => 2.6.31.15.28)
   linux-headers-generic (2.6.31.14.27 => 2.6.31.15.28)
   linux-image-generic (2.6.31.14.27 => 2.6.31.15.28)
   mythbrowser (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythflix (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythgallery (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythgame (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythmovies (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythmusic (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythnews (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-backend (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-frontend (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-transcode-utils (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythvideo (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythweather (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
The following packages will be upgraded:
   libmyth-perl (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   libmyth-python (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mytharchive (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mytharchive-data (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-backend-master (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-common (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-database (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-blootube-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-blueosd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-graphite (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-iulius-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-metallurgy (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-mono-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-mythbuntu (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-projectgrayhem-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-retro-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-theme-titivillus-osd (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythtv-themes (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   mythweb (0.22.0+fixes22750-0ubuntu0+mythbuntu3 => 0.22.0+fixes22936-0ubuntu0+mythbuntu3)
   nvidia-185-modaliases (185.18.36-0ubuntu9 => 185.18.36-0ubuntu9+ppa2)
21 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 43.7MB of archives.
After this operation, 28.7kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Odd. Perhaps try an "apt-get dist-upgrade -s", to simulate a dist-upgrade and see if it would remove any packages, or if it wants to install new ones.

---

### Post by ZedThou on 2009-12-04
Thanks for the suggestion, is nvidia-185-libvdpau the problem here? If I do a dist-upgrade then it seems the problem might just work itself out.

```

$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nvidia-185-libvdpau
The following NEW packages will be installed:
  libvdpau1 linux-headers-2.6.31-15 linux-headers-2.6.31-15-generic linux-image-2.6.31-15-generic
The following packages will be upgraded:
  libmyth-0.22-0 libmyth-perl libmyth-python linux-generic linux-headers-generic linux-image-generic linux-libc-dev mytharchive mytharchive-data mythbrowser mythflix mythgallery
  mythgame mythmovies mythmusic mythnews mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-frontend mythtv-theme-blootube-osd mythtv-theme-blueosd
  mythtv-theme-graphite mythtv-theme-iulius-osd mythtv-theme-metallurgy mythtv-theme-mono-osd mythtv-theme-mythbuntu mythtv-theme-projectgrayhem-osd mythtv-theme-retro-osd
  mythtv-theme-titivillus-osd mythtv-themes mythtv-transcode-utils mythvideo mythweather mythweb nvidia-185-modaliases
38 upgraded, 4 newly installed, 1 to remove and 0 not upgraded.
Inst libmyth-0.22-0 [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic) []
Remv nvidia-185-libvdpau [185.18.36-0ubuntu9] []
Inst libvdpau1 (0.2-0ubuntu1~ppa2 Ubuntu:9.10/karmic)
Inst linux-image-2.6.31-15-generic (2.6.31-15.50 Ubuntu:9.10/karmic-updates)
Inst mythtv-common [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-database [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-frontend [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-transcode-utils [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst libmyth-perl [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-backend [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-backend-master [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst libmyth-python [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst linux-generic [2.6.31.14.27] (2.6.31.15.28 Ubuntu:9.10/karmic-updates) []
Inst linux-image-generic [2.6.31.14.27] (2.6.31.15.28 Ubuntu:9.10/karmic-updates)
Inst linux-headers-2.6.31-15 (2.6.31-15.50 Ubuntu:9.10/karmic-updates)
Inst linux-headers-2.6.31-15-generic (2.6.31-15.50 Ubuntu:9.10/karmic-updates)
Inst linux-headers-generic [2.6.31.14.27] (2.6.31.15.28 Ubuntu:9.10/karmic-updates)
Inst linux-libc-dev [2.6.31-15.50] (2.6.31-16.52 Ubuntu:9.10/karmic-security)
Inst mytharchive-data [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mytharchive [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythbrowser [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythflix [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythgallery [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythgame [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythmovies [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythmusic [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythnews [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-blootube-osd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-blueosd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-graphite [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-iulius-osd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-metallurgy [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-mono-osd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-mythbuntu [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-projectgrayhem-osd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-retro-osd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-theme-titivillus-osd [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythtv-themes [1:0.22.0+fixes22750-0ubuntu0+mythbuntu3] (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythvideo [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythweather [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst mythweb [0.22.0+fixes22750-0ubuntu0+mythbuntu3] (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Inst nvidia-185-modaliases [185.18.36-0ubuntu9] (185.18.36-0ubuntu9+ppa2 Ubuntu:9.10/karmic)
Conf libvdpau1 (0.2-0ubuntu1~ppa2 Ubuntu:9.10/karmic)
Conf libmyth-0.22-0 (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf linux-image-2.6.31-15-generic (2.6.31-15.50 Ubuntu:9.10/karmic-updates)
Conf mythtv-common (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-database (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-frontend (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-transcode-utils (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf libmyth-perl (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-backend (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-backend-master (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf libmyth-python (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf linux-image-generic (2.6.31.15.28 Ubuntu:9.10/karmic-updates)
Conf linux-generic (2.6.31.15.28 Ubuntu:9.10/karmic-updates)
Conf linux-headers-2.6.31-15 (2.6.31-15.50 Ubuntu:9.10/karmic-updates)
Conf linux-headers-2.6.31-15-generic (2.6.31-15.50 Ubuntu:9.10/karmic-updates)
Conf linux-headers-generic (2.6.31.15.28 Ubuntu:9.10/karmic-updates)
Conf linux-libc-dev (2.6.31-16.52 Ubuntu:9.10/karmic-security)
Conf mytharchive-data (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mytharchive (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythbrowser (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythflix (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythgallery (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythgame (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythmovies (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythmusic (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythnews (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-blootube-osd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-blueosd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-graphite (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-iulius-osd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-metallurgy (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-mono-osd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-mythbuntu (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-projectgrayhem-osd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-retro-osd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-theme-titivillus-osd (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythtv-themes (1:0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythvideo (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythweather (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf mythweb (0.22.0+fixes22936-0ubuntu0+mythbuntu3 Ubuntu:9.10/karmic)
Conf nvidia-185-modaliases (185.18.36-0ubuntu9+ppa2 Ubuntu:9.10/karmic)

```

---

### Post by tgm4883 on 2009-12-04
Yep, thats the problem it looks like

---


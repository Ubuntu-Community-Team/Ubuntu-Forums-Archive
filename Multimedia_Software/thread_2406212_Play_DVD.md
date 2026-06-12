---
title: "Play DVD"
date: 2018-11-17
forum: Multimedia Software
---

### Post by zkab on 2018-11-17
I have Ubuntu 18.04.1 LTS and followed the guide [https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)
Still I can't play a DVD.
What is missing?

---

### Post by #&amp;thj^% on 2018-11-17
what shows from:
```
apt policy libdvdread4 libdvdnav4 libdvdcss2
```

This is how I install the works: (Code now fixed from the errors shown below)
```
echo 'deb http://download.videolan.org/pub/debian/stable/ /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
echo 'deb-src http://download.videolan.org/pub/debian/stable/ /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
wget -O - http://download.videolan.org/pub/debian/videolan-apt.asc | sudo apt-key add - &&
sudo apt-get update &&
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 ubuntu-restricted-extras gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
```

---

### Post by zkab on 2018-11-17
apt command gaves this ...

apt policy libdvdread4 libdvdnav4 libdvdcss2
```
libdvdread4:
  Installed: 6.0.0-1
  Candidate: 6.0.0-1
  Version table:
 *** 6.0.0-1 500
        500 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
libdvdnav4:
  Installed: 6.0.0-1
  Candidate: 6.0.0-1
  Version table:
 *** 6.0.0-1 500
        500 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages
        100 /var/lib/dpkg/status
libdvdcss2:
  Installed: 1.4.2-1~local
  Candidate: 1.4.2-1~local
  Version table:
 *** 1.4.2-1~local 100
        100 /var/lib/dpkg/status
     1.2.13-0 500
        500 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  Packages
```

When I ran your commands I got following:

```
echo 'deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
> echo 'deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /' | sudo tee -a /etc/apt/sources.list.d/libdvdcss.list &&
> wget -O - [http://download.videolan.org/pub/debian/videolan-apt.asc](http://download.videolan.org/pub/debian/videolan-apt.asc) | sudo apt-key add - &&
> sudo apt-get update &&
> sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 libavcodec-extra-53 libavformat-extra-53 libavutil-extra-51 libpostproc-extra-52 libswscale-extra-2 ubuntu-restricted-extras gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
--2018-11-17 17:26:09--  [http://download.videolan.org/pub/debian/videolan-apt.asc](http://download.videolan.org/pub/debian/videolan-apt.asc)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1934 (1,9K) [application/octet-stream]
Saving to: ‘STDOUT’

-                                                                      100%[==========================================================================================================================================================================>]   1,89K  --.-KB/s    in 0s      

2018-11-17 17:26:09 (498 MB/s) - written to stdout [1934/1934]

OK
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic InRelease                                                                                                                                                                              
Hit:3 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                                                                                                                                                                                                      
Hit:4 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                                                                                                                                                                                                    
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83,2 kB]                                                                                                                                                                                       
Hit:6 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) bionic InRelease                                                                                                
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                                                                                             
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                  
Ign:9 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  InRelease                                                                                             
Hit:10 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  Release                                                                         
Hit:11 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) bionic InRelease                                                               
Hit:12 [http://ppa.launchpad.net/phoerious/keepassxc/ubuntu](http://ppa.launchpad.net/phoerious/keepassxc/ubuntu) bionic InRelease                                     
Hit:13 [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu) bionic InRelease
Hit:14 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) bionic InRelease         
Hit:16 [http://ppa.launchpad.net/webupd8team/terminix/ubuntu](http://ppa.launchpad.net/webupd8team/terminix/ubuntu) bionic InRelease
Fetched 83,2 kB in 1s (99,7 kB/s)                    
Target Sources (Sources) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:2 and /etc/apt/sources.list.d/libdvdcss.list:4
Target Sources (Sources) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:2 and /etc/apt/sources.list.d/libdvdcss.list:6
Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
Reading package lists... Done
W: Target Sources (Sources) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:2 and /etc/apt/sources.list.d/libdvdcss.list:4
W: Target Sources (Sources) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:2 and /etc/apt/sources.list.d/libdvdcss.list:6
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
W: Target Sources (Sources) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:2 and /etc/apt/sources.list.d/libdvdcss.list:4
W: Target Sources (Sources) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:2 and /etc/apt/sources.list.d/libdvdcss.list:6
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:3
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
W: Target Translations (en_US) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/libdvdcss.list:1 and /etc/apt/sources.list.d/libdvdcss.list:5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec-extra-53 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libavcodec-extra-53' has no installation candidate
E: Unable to locate package libavformat-extra-53
E: Unable to locate package libavutil-extra-51
E: Unable to locate package libpostproc-extra-52
E: Unable to locate package libswscale-extra-2
```

---

### Post by #&amp;thj^% on 2018-11-17
Those that are not found are now included with "ffmpeg" ;)
```
E: Package 'libavcodec-extra-53' has no installation candidate
E: Unable to locate package libavformat-extra-53
E: Unable to locate package libavutil-extra-51
E: Unable to locate package libpostproc-extra-52
E: Unable to locate package libswscale-extra-2 
```
I updated my code now for 18.04, I just keep rolling into the next release so I seldom have to run that code.
But your libdvdcss2 install is different than mine:
```
libdvdcss2:
  Installed: 1.2.13-0
  Candidate: 1.2.13-0
  Version table:
 *** 1.2.13-0 500
        500 http://download.videolan.org/pub/debian/stable  Packages
        100 /var/lib/dpkg/status

```
EDIT: I just now caught this:
I also don't have this installed:
```
apt policy libdvd-pkg
libdvd-pkg:
  Installed: (none)
  Candidate: 1.4.2-1-1
  Version table:
     1.4.2-1-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages
        500 http://archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages

```
I have no problems watching my DVD collection.

---

### Post by Autodave on 2018-11-17
Have you tried any other DVDs to see if they play?  Some of the newer ones are actually written (burned) with a bad sector at the very beginning.  A regular DVD player just ignores this and looks for one that it can read.  A PC DVD stops right there.  I have a couple here that will not play on any OS: Win7, Win10, Mac.  However, they work just fine in my DVD player that is hooked up to the TV.

---

### Post by zkab on 2018-11-18
I tried to play it on a Windows10 computer with VLC ... it worked

---

### Post by mc4man on 2018-11-18
What player are you trying to use?
If it's the snap version of vlc it's likely it can't do commercial dvd's as libdvdcss2 is not included in the snap & it can't access the the system libdvdcss2.
ck. - 
```
snap list
```

---

### Post by zkab on 2018-11-18
I have the full version from VLC ...

---

### Post by mc4man on 2018-11-18
> **zkab said:**
> I have the full version from VLC ...

Well then open vlc in a terminal, try to play a dvd, check the terminal output.

---


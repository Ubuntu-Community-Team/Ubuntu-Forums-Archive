---
title: "Package manager is stuck in 18.04"
date: 2018-08-30
forum: Multimedia Software
---

### Post by jlh68 on 2018-08-30
This is the notice I got and Package Manager is lockedup

E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
I have not found a way to unlock Package Manager, so I cannot install any more applications. 

I was trying to download the Restricted Extras and it got stuck and now I get th above message, with no way to clear it out and start over.  I can not even download any thing else.

---

### Post by Frogs Hair on 2018-08-30
Close all package management applications, run the following commands, and post any errors.

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt update
```

---

### Post by jlh68 on 2018-08-30
sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily InRelease                       
Err:3 [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) yakkety-getdeb InRelease                
  Could not connect to archive.getdeb.net:80 (144.76.200.19). - connect (111: Connection refused)
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]    
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]     
Hit:6 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) xenial InRelease         
Hit:7 [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) xenial InRelease          
Hit:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [319 kB]
Hit:11 [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) xenial InRelease        
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [132 kB] 
Ign:13 [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) xenial InRelease   
Ign:14 [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) xenial InRelease     
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [219 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [72.8 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [550 kB]
Hit:18 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease       
Err:19 [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) xenial Release     
  404  Not Found
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [841 kB]
Err:21 [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) xenial Release       
  404  Not Found
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [477 kB]
0% [20 Packages 530 kB/841 kB 63%] [22 Packages 241 kB/477 kB 51%]             
0% [20 Packages 530 kB/841 kB 63%] [22 Packages 241 kB/477 kB 51%]

---

### Post by jlh68 on 2018-08-30
Ops wrong computer.  That output is from my 16.04 Laptop.  I need to do the 18.04  netbook

---

### Post by jlh68 on 2018-08-30
sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]    
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse i386 Packages [144 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 Packages [151 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse Translation-en [108 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse DEP-11 48x48 Icons [8,931 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/multiverse DEP-11 64x64 Icons [225 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 Packages [1,608 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 Packages [1,444 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse Translation-en [996 B]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [305 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [273 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [3,928 B]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [3,772 B]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse Translation-en [2,376 B]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse DEP-11 48x48 Icons [29 B]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse DEP-11 64x64 Icons [2,638 B]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [172 kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [173 kB]
Fetched 1,801 kB in 6s (294 kB/s)

---

### Post by Frogs Hair on 2018-08-30
I don't see any errors .  ```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

---

### Post by jlh68 on 2018-08-31
Either some code you gave me or some one else, part of the problem was gone, which allowed me to use Synaptic to "reinstall" the ttf-mscorefons-installer" and that has cleared up my problem. 

Thanks for your support.  I wish I knew what process I went through to clear it up.

---


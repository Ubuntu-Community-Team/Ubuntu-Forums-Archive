---
title: "VDPAU patch installation problem"
date: 2009-03-02
forum: Mythbuntu
---

### Post by erotomanic on 2009-03-02
I was trying to install the VDPAU patch from the repository provided by Jean-Yves.  I followed the instructions provided then did:

aptitude update
aptitude safe-upgrade

It told me that some of the Myth packages were being held back and some were being automatically held back.  It would only allow me to update 2 packages - libmyth-python and libmyth-perl.  I did not update only those as I thought it might screw something up.

I am currently running 8.04 with the latest fixes branch (now removed from my sources list) and have a NVIDIA 8400 card which I had already manually updated to the latest drivers 180.35.  I will post the exact message from aptitude later.  Anybody know what is going on?  Thanks...

---

### Post by nickrout on 2009-03-02
give us the exact error message, should be fixable from there.

---

### Post by erotomanic on 2009-03-03
ok, here is what I get:

et@et-pc:~$ sudo aptitude safe-upgrade
[sudo] password for et: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libmyth-0.21-0 mythtv-backend mythtv-common mythtv-database 
  mythtv-transcode-utils 
The following packages have been kept back:
  mplayer mythtv mythtv-backend-master mythtv-frontend 
The following packages will be upgraded:
  libmyth-perl libmyth-python tzdata 
3 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 767kB of archives. After unpacking 53.2kB will be freed.
Do you want to continue? [Y/n/?]

---

### Post by nickrout on 2009-03-03
It may be that -fixes has a version later than the vdpau branch? What version of mythtv do you have from fixes?

dpkg -l|grep mythtv-frontend

jean-yves version appears to be at 20018

---

### Post by erotomanic on 2009-03-04
yeah, that crossed my mind too but it looks like the version is lower

ii  mythtv-frontend                       0.21.0+fixes19878-0ubuntu0+mythbu

---

### Post by theophile on 2009-03-05
I'm having the same problem. I added the VDPAU repo, updated, and tried to upgrade:

```
root@farmer:/mnt/sdd# aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libid3-3.8.3-dev 
The following packages have been automatically kept back:
  libmyth-0.21-0 mythtv-backend mythtv-common mythtv-database mythtv-transcode-utils 
The following packages have been kept back:
  libmyth-dev mythtv mythtv-backend-master mythtv-frontend 
The following packages will be upgraded:
  curl kdelibs-data kdelibs4c2a libcurl3 libcurl3-gnutls libcurl4-openssl-dev libmyth-perl libmyth-python network-manager-gnome tzdata 
10 packages upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
Need to get 19.4MB of archives. After unpacking 918kB will be freed.
Do you want to continue? [Y/n/?] 
```

Has anyone figured out how to make this work?

---

### Post by mGSz on 2009-03-06
I had similar problems when using Ubuntu 8.04. I had to upgrade to 8.10 before I was able to use repositories by Jean-Yves.

---

### Post by erotomanic on 2009-03-17
Ok, with the new updates to Jean-Yves' repositories, I was able to to get this working with 8.04.  I followed the instructions he has on his site, then had to follow with:

sudo apt-get update
sudo apt-get dist-upgrade

NOTE:  apt-get upgrade would not work as it caused some packages to be held back


Thanks Jean-Yves, great work!!

---


---
title: "cant install xbmc"
date: 2014-06-11
forum: Multimedia Software
---

### Post by bill43 on 2014-06-11
hi i am trying to install xbmc on ubuntu 12.04 mate desktop environment when i try i get error
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xbmc : Depends: xbmc-bin (>= 2:11.0~git20120423.cd20772-1) but it is not going to be installed
        Depends: xbmc-bin (< 2:11.0~git20120423.cd20772-1.1~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```
i have tryed fixing broken packages with synaptic 
and
sudo dpkg --configure -a --force-all

any ideas thanks?

---

### Post by bill43 on 2014-06-11
im not 100% but i have concluded that im am getting these errors due to using 12.04 which is now discontinued so when im using apt-get it is downloading the latest version which wont install on 12.04,i used synaptec to get an older xbmc and it installed fine would like to upgrade to 14.04 but there are just far to many bugs at the moment tought i would post the solution in case it was of help to others

---

### Post by Vladlenin5000 on 2014-06-11
The official method described here [http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux](http://wiki.xbmc.org/index.php?title=Installing_XBMC_for_Linux) clearly mentions the need to install *python-software-properties*, *pkg-config* and *software-properties-common*. Have you?
I've so far installed XBMC in over than a dozen different machines running 14.04 using those instructions and had 0 (zero) issues.

---


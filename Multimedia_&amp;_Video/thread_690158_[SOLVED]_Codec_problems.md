---
title: "[SOLVED] Codec problems"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by skippi90 on 2008-02-07
I installed Ubuntu Gutsy last night, the first time I've used Linux. After disabling ipv6, I got my wireless network to connect to the internet.

However, I can't seem to install codecs or programs. I always get asked to reload the list.

I have heard about needing to add repositories etc. but I need a guide of what to do from the start.

Please help. I need a problem specific answer. Thanks in advance.


---------------------------
Stevie

---

### Post by PmDematagoda on 2008-02-07
Go to Software Sources in System>Administration>Software Sources and enable all except for the CD-ROM in the Ubuntu Software tab, after that is done, close the window and reload the sources list as instructed, after that is done you should be able to install the codecs.

---

### Post by skippi90 on 2008-02-07
OK. Thanks for the quick reply. I'm in college at the moment so I'll give that a go when I get home.


Thanks again.

---

### Post by skippi90 on 2008-02-07
OK, I've done as suggested but the file downloads are failing.

[[IMG]http://img502.imageshack.us/img502/1184/screenshotdownloadingpaik7.th.png[/IMG]](http://img502.imageshack.us/my.php?image=screenshotdownloadingpaik7.png)

Any help towards a solution is greatly appreciated.

---

### Post by PmDematagoda on 2008-02-07
Regardless of the failing downloads, did the sources list reload succeed without any errors appearing?

---

### Post by skippi90 on 2008-02-07
No. Although I've just edited the source list to uncomment the addresses so I'll see if that works.

---

### Post by PmDematagoda on 2008-02-07
Were the entries in the sources.list file commented out? If so, then that would have been the problem.

---

### Post by skippi90 on 2008-02-07
Yeah they were but even now in the show progress of single files box, they are failing.

Maybe I haven't uncommented the list correctly?

COuld you post what the source list should be like? Thanks.

---

### Post by PmDematagoda on 2008-02-07
Could you post the output of:-
```
cat /etc/apt/sources.list
```

Could you also post some details about your internet connection, specifically if you are behind a proxy or not.

---

### Post by skippi90 on 2008-02-07
```
steven@steven-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted

```


As for the internet connection, I'm pretty certain I'm not behind a proxy.

---

### Post by PmDematagoda on 2008-02-07
Your sources.list file looks good, I simply do not understand why you cannot reload the sources list.

I am really sorry, but unfortunately I cannot help further, I hope someone would be able to come along and clear things up.

---

### Post by skippi90 on 2008-02-07
OK. Thanks for your help.

---

### Post by skippi90 on 2008-02-07
Sorted!

I used "FInd Best Server" and it reccomended a Thailand server. EVerything worked from there. :)

---


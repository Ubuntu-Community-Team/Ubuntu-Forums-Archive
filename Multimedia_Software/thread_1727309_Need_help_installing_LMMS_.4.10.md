---
title: "Need help installing LMMS .4.10"
date: 2011-04-12
forum: Multimedia Software
---

### Post by stephenstop on 2011-04-12
I have LMMS .4.5 but i saw that there is a .4.10,(is .10 better?)and i downloaded the .4.10.tar.bz2 from [http://sourceforge.net/projects/lmms/files/lmms/0.4.10/,I](http://sourceforge.net/projects/lmms/files/lmms/0.4.10/,I) do not know how to make it work from there
I have very limited linux and computer abilities.I have ubuntu 10.04.The .4.10.tar.bz2 has been extracted by the archive manager but I really need help.I would very much appreciate it.

Stephen Ankrum

---

### Post by Enigmapond on 2011-04-12
There is really no difference..just updated a bit. Do yourself a huge favour and avoid the headache. Update this ppa in the terminal:

```
sudo add-apt-repository ppa:kxstudio-team/music
```

and update/upgrade. This will give you 0.4.9 which is the current stable version and still works very well.

Cheers!

---

### Post by stephenstop on 2011-04-12
Thanks man I really appreciate it.I'm so behind the times.Are their any differences between .4.9 and .4.5?What is a ppa,i read the definition but i need like a "linux for dummies" book or somin.Thanks again

---

### Post by Enigmapond on 2011-04-12
There are no big differences between the two versions. Just updated the files and a bit of the interface. Sometimes it's just an upgrade to keep up with the current kernel. A PPA is a packaging archive where developers update their wares to be available to the public. Sometimes it's better to update from the PPA itself as the Ubuntu repos are a bit slow on occasion as getting them.When you upgrade to the PPA I posted, you will get updates on LMMS and other apps that are involved with ubuntustudio-audio. This isn't a developers PPA but is a centralized PPA put together by the studio team to make it easy for musicians to update their apps. So to make it easy, open a terminal and do this:

```
sudo add-apt-repository ppa:kxstudio-team/music
```This updates to the PPA and imports the key. Then:

```
sudo apt-get update && sudo apt-get upgrade
```This updates your system to accept new apps from the ppa and upgrades to the new versions.
I hope this answers your question.

---

### Post by stephenstop on 2011-04-12
yea you definitely answered my question thank you.I did both commands in terminal and it scrolled through a bunch of stuff and now says


[sudo] password for owner: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A809F6C307B583133B3891B287538FEDDF8063EB
gpg: requesting key DF8063EB from hkp server keyserver.ubuntu.com
gpg: key DF8063EB: public key "Launchpad PPA for KXStudio Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
owner@owner-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/kxstudio-team/music/ubuntu/](http://ppa.launchpad.net/kxstudio-team/music/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://ppa.launchpad.net/owner/lmms/ubuntu/](http://ppa.launchpad.net/owner/lmms/ubuntu/) lucid/main Translation-en_US   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/owner/ppa/ubuntu/](http://ppa.launchpad.net/owner/ppa/ubuntu/) lucid/main Translation-en_US    
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,086B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Get:8 [http://dl.google.com](http://dl.google.com) stable/main Packages [737B]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [295B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:10 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [1,527B]
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:11 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [1,661B]
99% [11 Packages lzma 0B]/usr/bin/lzma: Decoder error
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
  Sub-process /usr/bin/lzma returned an error code (1)
Fetched 22.7kB in 1min 50s (204B/s)
W: Failed to fetch [http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.lzma](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.lzma)  Sub-process /usr/bin/lzma returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.
owner@owner-laptop:~$ 
Is this what it was supposed to do?I have a few other questions if you have the time.Thanks so much.
Stephen Ankrum

---

### Post by Enigmapond on 2011-04-12
Well no...but none of those errors have anything to do with the PPA I just gave you. First do sudo apt-get upgrade in the terminal. This will upgrade your LMMS and others. Regarding the errors, I have no idea. Seems you have a few sources that either are down or in correct.

Run this command in the terminal and post the output here...but post them between the "code" bbcodes.. 
cat /etc/apt/sources.list
```
like this
```

---

### Post by stephenstop on 2011-04-12
hey sorry Im confused Delight thyself also in the LORD: and he shall give thee the desires of thine heart.  what should i type into the terminal?
thanks

---

### Post by stephenstop on 2011-04-12
HA i did not mean to type the bible verse in there.I put cat /etc/apt/sources.list in the terminal,you want the stuff that came when i hit enter and how do i put that box in that you use?

---

### Post by Enigmapond on 2011-04-12
These are two separate issues. First let's take care of upgrading your app...the reason for this thread.. :) Open the terminal and do:

```
sudo apt-get update
```After everything updates and you get a terminal prompt again do:

```
cat /etc/apt/sources.list
```And post the output here. When you post it here, look on the top of the reply field and you see "#". Click that and copy/paste the terminal output to that command between the two "code" brackets...

```
and it will look like this
```

---

### Post by stephenstop on 2011-04-12
[code]owner@owner-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
owner@owner-lapto

here it is

---

### Post by Enigmapond on 2011-04-12
Well I can't see anything in there that would cause the errors. Did your LMMS update? If it did, mark this thread as solved and open another in General Help and post the errors you initially got to see if anyone else can pick up on it. I'm just a musician and P/T Geek...LOL Sorry.

---

### Post by stephenstop on 2011-04-12
```

```owner@owner-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
owner@owner-laptop:~$ 
```

```
here it is,thanks alot

---

### Post by stephenstop on 2011-04-12
Ok how would i know it updated?what is the .4.10 version and thanks ill put it there.What kind of music do you make?Thanks for your help
stephen

---

### Post by stephenstop on 2011-04-12
also do you know what uncomment means when in my terminal?

---

### Post by Yellow Pasque on 2011-04-12
uncomment = remove leading '#' from a line

Also, look in /etc/apt/sources.list.d for more source list files.

---

### Post by Enigmapond on 2011-04-12
> **stephenstop said:**
> Ok how would i know it updated?what is the .4.10 version and thanks ill put it there.What kind of music do you make?Thanks for your help
stephen

Open LMMS...Right on the title bar, it gives the version. Providing you ran just the "UPGRADE" command...it will say " LMMS 0.4.9".

[www.soundclick.com/enigmapond](www.soundclick.com/enigmapond)

Have a listen.

---

### Post by stephenstop on 2011-04-12
hey thanks again,you have no idea how much I appreciate the help.How and why would I want to remove # and im not sure what you mean by the apt/source part.

also i did run the command but my lmms is still .4.5
thanks

---

### Post by stephenstop on 2011-04-12
Hey I still need help if you dont mind.LMMS did not update

---

### Post by Yellow Pasque on 2011-04-12
```
cat /etc/apt/sources.list.d/*
```

---

### Post by stephenstop on 2011-04-13
thanks i tried that command but it did not work.I have limited knowledge and really need help.
thank you so much.
stephen

---


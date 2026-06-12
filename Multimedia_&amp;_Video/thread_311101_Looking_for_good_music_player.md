---
title: "Looking for good music player"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by geek_Man on 2006-12-02
Hey all, I'm looking for a (free) music player that I can play my DRM'd music with. I've downloaded a LOT of music from the iTunes Music Store and want to play them on Ubuntu. I've heard that Amarok is a good program to use, but I can't install it for some reason. Same thing with Gtkpod, can't install it. Right now I have Beep and Rhythmbox, but they can't play my DRM'd music. Even if I can download some modules or codecs, that would be good. Thanks to all in advance!

---

### Post by deep.tinker77 on 2006-12-02
Is your system giving you a specific reason on what's going wrong with the install of Amarok and Gtkpod?. Double check your sources.list to make sure you have all of the correct repositories. Are you using Automatix? Need more info.

---

### Post by geek_Man on 2006-12-02
When I try to install through the terminal (with aptitude) it tells me that no candidate version was found for Amarok. When I try with Add/Remove Applications (I don't know the exact name) it tells me it is not availible in any software channel. When I click the Advanced button and try it tells me it has unresolvable dependencies. Pretty much the same thing for Gtkpod. Also, I don't know what Automatix is or where source.list is. Hope ths helps.

---

### Post by odei on 2006-12-02
This is my current /etc/apt/sources.list and I just installed gtkpod and amarok fine.
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

# Repository for wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main
```

---

### Post by geek_Man on 2006-12-02
Thanks Odei, I got Amarok installed, I just have to figure out how to play my DRM'd music. You wouldn't know how to do that, would you?

---

### Post by Shatrat on 2006-12-02
You might want to look into [http://hymn-project.org/](http://hymn-project.org/) and do some googling.

The ideal solution is not to purchase DRMed anything, ever.

---

### Post by geek_Man on 2006-12-03
Well, obviously it's a little late for that, but I'll check out the links. Thanks!

---


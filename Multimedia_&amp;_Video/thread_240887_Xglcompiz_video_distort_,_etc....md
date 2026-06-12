---
title: "Xgl/compiz video distort , etc..."
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by nrayever on 2006-08-21
hi everyone:

a month a go, i installed xgl/compiz on my inspiron 9400 using automatix bleeder. my laptop has a nvidia 7800, so there's no problem that. so i select xgl session and then i run the command "toggle-compiz-nvidia". when i toggle to compiz, x gets weird.

the edges of a window program disappear. some video distorts occur while moving a program through the desktop, icons disappear, etc... no program got free of this problem.

here is a screenshot of my problem.

is there any way to solve this?? because it's really annoying to have these distorts. i can't enjoy to have xgl/compix installed :cry: :cry: 

need some help, please!! i can't figure how to solve it. ](*,) ](*,) ](*,)

sincerly nrayever

---

### Post by arnieboy on 2006-08-21
> **nrayever said:**
> hi everyone:

a month a go, i installed xgl/compiz on my inspiron 9400 using automatix bleeder. my laptop has a nvidia 7800, so there's no problem that. so i select xgl session and then i run the command "toggle-compiz-nvidia". when i toggle to compiz, x gets weird.

the edges of a window program disappear. some video distorts occur while moving a program through the desktop, icons disappear, etc... no program got free of this problem.

here is a screenshot of my problem.

is there any way to solve this?? because it's really annoying to have these distorts. i can't enjoy to have xgl/compix installed :cry: :cry: 

need some help, please!! i can't figure how to solve it. ](*,) ](*,) ](*,)

sincerly nrayever
do u have the compiz repo added?
paste your sources.list here

---

### Post by nrayever on 2006-08-22
> **arnieboy said:**
> do u have the compiz repo added?
paste your sources.list here

hi arnie:

here it's my sources.list

```
deb http://mx.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://mx.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://mx.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://www.getautomatix.com/apt dapper main

deb http://www.beerorkid.com/compiz/ dapper main

deb http://nightlies.videolan.org/build/dapper-i386 /

## Main
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

deb http://exodus.xmms.se/debian dapper main

#Cinelerra
#deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./

```

i think that is the one referring to beerorkid, no??

nrayever

---


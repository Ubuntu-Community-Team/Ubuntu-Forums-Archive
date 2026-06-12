---
title: "cinelerra"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by tubunu on 2007-04-21
How do I get it to install on Feisty? I had no problems installing it on Egdy. I need to finish editing a film I started on Edgy and now I don't know how to install it. Any help appreciated! :)

---

### Post by tubunu on 2007-04-21
Okay, that was as easy as going to Flavor 8 site and following the instructions there: 

Edit your /etc/apt/sources.list, and add the following repository:
```
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
```

On the command line, run the following:
sudo apt-get update
sudo apt-get install cinelerra

:guitar:

---

### Post by walkingbeard on 2007-04-21
I just installed it from the repository listed for Edgy on the Cinelerra-CV site.  Seems to be working just fine.

---

### Post by florian_roger on 2007-04-26
Hi!
New on Linux, I was using >Cinellera on Edgy, which was working well, and I installed yesterday Feisty. I can install Cinelerra but it's not working.
I followed the tubunu's way but there is nothing to do...

Mysources.list is:

> ## DÉPÔTS OFFICIELS
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
#deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

## Commercial
deb [http://archive.canonical.com/](http://archive.canonical.com/) feisty-commercial main

## MEDIBUNTU
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## lprod (depot pour la video)
deb [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./
deb-src [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./

when I enter the command ```
dpkg -l cinelerra
```
it results  > Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé
|/ Err?=(aucune)/H=à garder/besoin Réinstallation/X=les deux (État,Err: majuscule=mauvais)
||/ Nom            Version        Description
+++-==============-==============-============================================
ii  cinelerra      2.1.0-2svn2007 An audio/video authoring tool

the end of the file given by the comand ```
strace cinelerra > /tmp/log 2>&1
```
is  > writev(2, [{"cinelerra", 9}, {": ", 2}, {"symbol lookup error", 19}, {": ", 2}, {"/usr/lib/libquicktimehv-1.6.0.so"..., 34}, {": ", 2}, {"undefined symbol: faacDecClose", 30}, {"", 0}, {"", 0}, {"\n", 1}], 10cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecClose
) = 99
exit_group(127)                         = ?
Process 9848 detached

Is it possible to install cinelerra on Feisty i86??
Thanks for help,
Florian

---

### Post by florian_roger on 2007-04-27
up! :rolleyes:

---

### Post by tubunu on 2007-04-29
I remember after I've done:

```
sudo apt-get update
sudo apt-get install cinelerra
```

I edited my sources list to include feisty. So instead of:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./

Copy this into your /etc/apt/sources.list:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

Then do sudo apt-get update and you should immediately get a cinelerra update (version 2.1) in your Adept Manager, install it and you should be able to run it. That's what I did and it works! :) Hope it helps you too.

---

### Post by pdowling on 2007-05-02
This is on the [Get Cinelerra page]("http://cv.cinelerra.org/getting_cinelerra.php") and has a section specifically for Feisty.

I just did a fresh install using those instructions and it seemed to work fine.  Only problem I had was an error related to shared memory.  The exact error I received and the fix are both described [here in the cinelerra manual wiki]("http://cv.cinelerra.org/docs/wiki/doku.php?id=english_manual:cinelerra_cv_en_20#freeing_more_shared_memory").  After that, no errors.

Haven't had a chance to play with it yet though.  Hopefully soon.

- Peter

---

### Post by resnasty on 2007-05-23
does all of this work for x64 as well??

---


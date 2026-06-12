---
title: "Brasero 100% fail rate"
date: 2008-05-23
forum: Multimedia Software
---

### Post by attercop on 2008-05-23
I have lots of coasters that Brasero, k3b etc has made for me. So far i've tried burning music CDs on my 8.04, which burns just enough onto the CD-R to ruin it without actually writing anything on it. And i tried burning the 8.04 ISO on 7.10 a few times without success. I now have to boot into an inferior OS every time i need to burn something. My Sony DVD +/- RW drive is nothing remarkable. Are any of them blacklisted? Anyone have any ideas?

---

### Post by 47_MasoN_47 on 2008-05-23
Brasero does the same thing for me in Hardy while it worked fine on the same PC with Gutsy.

I just use the CD writing application that is built into Ubuntu and it works fine.  It can handle .iso files and such and so far I haven't had any coasters.

---

### Post by attercop on 2008-05-25
Nothing works for me in Hardy. It's always a coaster. And it must be the software as everything is good outside of Ubuntu.

---

### Post by fermin on 2009-01-11
Im using Ubuntu 8.10 Intrepid Ibex in my laptop and desktop computers and couldnt burn an ISO image. I tried with **Brasero, Nautilus and GnomeBaker**. None of them worked. It had previosly been working all right with this same Ubuntu Version (and previous ones since 7.10 Gutsy) and on both computers. After re downloading the ISO image and trying with the three programs in both computers I was on the brink of madness ](*,)when it occurred to me to **try another brand of CDs**: case solved. I have been able to burn whatever i like as long as I use this brand that works. The brand that didnt work for me was Memorex CD-R and the brand that DOES work for me is FUJIFILM CD-R. Now I havent tried but these two brands and my hardware and software WAS working with Memorex CDs about a week ago (I have a 50 CD tower used in half now). So i reckon it is **neither a Gutsy/Hardy/Intrepid issue nor a Brasero/GnomeBaker/Nautilus/K3b issue**, but this problem keeps coming up in the forums. It may have to do with an update of the *linux kernel*. That's my guess. It is a certainly annoying bug and **MUST be tracked down**.

---

### Post by albinootje on 2009-01-11
> **attercop said:**
> I have lots of coasters that Brasero, k3b etc has made for me. So far i've tried burning music CDs on my 8.04, which burns just enough onto the CD-R to ruin it without actually writing anything on it. And i tried burning the 8.04 ISO on 7.10 a few times without success. I now have to boot into an inferior OS every time i need to burn something. My Sony DVD +/- RW drive is nothing remarkable. Are any of them blacklisted? Anyone have any ideas?

There was a problem with some burners in Hardy. 
(That is, that I've read, that the problem was not with all burners)

I came across that myself.
The work-around was to boot with the all_generic_ide option.

Here are two somewhat related bug reports, which also mentioned the all_generic_ide kernel boot parameter :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200337/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200337/comments/22)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187807](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187807)

Lately I've also seen some people recommend to remove the buggy wodim, and replace it with cdrecord.

---

### Post by Alejandro Nova on 2009-01-12
I have anger against wodim. Wodim is a fork risen from hate against cdrecord. Everytime I look at wodim and look at how it tries to mock cdrecord, replace cdrecord, and seek-and-destroy cdrecord (enable the Burning Team PPA in Ubuntu, *deb [http://ppa.launchpad.net/ubuntu-burning/ubuntu](http://ppa.launchpad.net/ubuntu-burning/ubuntu) intrepid main* in your sources.apt file, install cdrecord, and see how wodim SILENTLY OVERWRITES IT) I remember gset-compiz, a program whose author ended deleting the entire Beryl forum and bringing hate to the holy war between Compiz and Beryl.

The latest cdrecord, provided by Jörg Schilling, is alpha55 (December 29th, 2008 ). That's 2 weeks ago. Compare that to the Intrepid Ibex wodim release, 1.1.8, released in May 2008. If you check out [http://lists.alioth.debian.org/pipermail/debburn-devel/](http://lists.alioth.debian.org/pipermail/debburn-devel/) , you'll notice that since February 2008 wodim is in maintenance mode, while cdrecord was busy adding BluRay support and other interesting things.

This is madness. I suggest you to do the following.

1. Check if you have genisoimage and wodim installed.
2. Add the Burning Team Ubuntu PPA to your sources.list. The DEB line is:

```
deb http://ppa.launchpad.net/ubuntu-burning/ubuntu intrepid main

```

3. Remove genisoimage and wodim using the following commands.

```
sudo dpkg --remove --ignore-depends=genisoimage genisoimage
sudo dpkg --remove --ignore-depends=wodim wodim
```

4. Install cdrecord and mkisofs

```
sudo apt-get install cdrecord mkisofs
```

5. Look for /usr/bin/cdrecord and /usr/bin/mkisofs. Rename them (to circumvent the seek-and-destroy mechanisms of wodim and genisoimage packages)

```
sudo su
# cd /usr/bin
# mv cdrecord cdrecord.real
# mv mkisofs mkisofs.real
```

6. Reinstall wodim and genisoimage. ANY BURNING SOFTWARE YOU HAVE WILL BE BROKEN TO APT UNLESS YOU DO THIS.

```
sudo apt-get install wodim genisoimage
```

7. Final rename.

```
sudo su
# cd /usr/bin
# mv cdrecord cdrecord.wodim
# mv mkisofs mkisofs.genisoimage
# mv mkisofs.real mkisofs
# mv cdrecord.real cdrecord
```

That's it. You have wodim and cdrecord side by side, with cdrecord being detected and used automagically by all your burning software, and with no broken packages. According to Jörg Schilling, your bug with your burner may have to do with a failed interaction between a post-2.6.8 kernel and the IDE subsystem, and was fixed in cdrecord, but was never fixed in wodim. If everything went well, you'll get this.

```
faeris@faeris:~$ cdrecord --version
Cdrecord-ProDVD-ProBD-Clone 2.01.01a50 (i686-pc-linux-gnu) Copyright (C) 1995-2008 J&#65533;rg Schilling

faeris@faeris:~$ cdrecord.wodim --version
Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd
Wodim 1.1.8
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling
```

---

### Post by Alejandro Nova on 2009-01-12
And, as a gift, this is Jörg Schilling warning, directly from [http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html) . As your burning is failing since Gutsy, one of these bugs may explain it.

[I]What are the problems when running programs from the broken fork?
#
In all programs of the fork that send SCSI commands, you may be unable to access any of the CD/DVD/Blu-Ray drives at all if you are on Linux-2.6.8.1 or later. This is due to a missing workaround for the Linux kernel interface change that happened with Linux-2.6.8.1.
#
In the cdrecord clone from the fork, messages have been removed that would warn you in case that you are not running cdrecord as root. As some of the SCSI commands used by cdrecord need root privileges, cdrecord may fail later with strange problems because of this hack. Note that cdrecord supports (and needs to support) many vendor unique features of drives (e.g. for optimized writing of CDs and DVDs). Linux filters away all vendor specific SCSI commands in case the program that sends them does not have root privileges. There are other non vendor unique commands that are filtered also.

The mature DVD support from the original cdrecord has been ripped off and replaced by something of very poor quality. The replacement code misses key features (like -atip extraction and printout). As a result the DVD code in the fork is not correctly parameterized.

All recent cdrecord enhancements like better CUE Sheet for CDs support and Blu-Ray support are missing in the clone.
#
The mkisofs clone from the fork is the worst of all. The web is full of bug reports for the clone.

The original mkisofs fixed dozens of bugs from the early days of mkisofs (1993-1997). These bugs are still present in the fork.

The original mkisofs added support for multi-extent files that may be > 4 GB (up to 8 TB) while the fork does not support more than 4 GB.

The original mkisofs added find(1) command line support into mkisofs via libfind and thus gives a lot new features that are important for people who like to use mkisofs for simple backups or like to avoid the need to create a copy of the tree that is going to be processed by mkisofs. This feature is missing in the fork.

The original mkisofs added support for Rock Ridge Version-1.12 and now supports correctly working hard links. This feature is missing in the fork.

The original mkisofs added support for correct link counts on all files and directories. This feature is missing in the fork.

The original mkisofs replaced the GNU getlongopt based CLI interface by something with much less bugs. The design for the mkisofs options from the early days introduced a lot of similar named long options. The old GNU getlongopt based code does not detect typo's in the options but rather finds the option with the longest substring that does not have a typo and assigns it a string parameter that contains the typo.

The original mkisofs added working support for UTF-8 based locales and support for iconv based translations. The clone claims to do the same but disabled key features from mkisofs with the attempt to support UTF-8 and may create images with incorrect file name lengths without even printing a warning.

The original mkisofs added much better UDF support (such as support for symlinks, userids/groupids and permissions as well as support for MacOS extensions). These features are missing in the fork.

The mkisofs clone will create unusable filesystems in some cases when Joliet is used. This is a bug that never existed in the original. [/I]

---

### Post by odduck on 2009-03-12
I tried to run through the fix given in post #6 but when I get to the step that calls for installing cdrecord and mkisofs, I get an error about the packages that are now broken because wodim and genisoimage are not installed and I can't move forward.  If someone could just help me work around this little step, it'd be much appreciated.

Here's the error message just in case:

> You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
brasero: Depends: wodim but it is not going to be installed
Depends: genisoimage but it is not going to be installed
dvd+rw-tools: Depends: genisoimage but it is not going to be installed
nautilus-cd-burner: Depends: genisoimage but it is not going to be installed
Depends: wodim but it is not going to be installed
ubuntu-desktop: Depends: genisoimage but it is not going to be installed
Recommends: totem-mozilla but it is not going to be installed
Recommends: wodim but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by odduck on 2009-03-12
Bump.

I've tried running the "--ignore-missing" and "-m" flags (which I realize are the same thing) when running the install command but to no avail.  Still getting the same error.

Is there any way to ignore these broken dependencies?

---

### Post by wolfen69 on 2009-03-12
did you run
```
sudo apt-get install -f
```?

---

### Post by odduck on 2009-03-12
> **wolfen69 said:**
> did you run
```
sudo apt-get install -f
```?

I think that will just install the packages that i'm trying to avoid at this stage of the "fix".

From what i've gathered, i want to have genisoimage and wodim off my system until after i've downloaded cdrecord and mkisofs and been able to temporarily rename them so as to circumvent wodim and genisoimage's search and destroy function.  problem is that apt-get doesn't want to let me install cdrecord and mkisofs because wodim and genisoimage aren't there.  If I try to install cdrecord and mkisofs without removing the other two from my system, then apt-get just selects the other two for reinstallation anyways.  So I'm stuck in a Catch-22 right now.

---

### Post by akwusmc on 2009-06-20
Bump -

I'm having the same problems ...... apt-get -f install gets me back to widom and genisoimage, which then replaces cdrecord and mkisofs.

Anyone have a solution?

aw

> **odduck said:**
> I think that will just install the packages that i'm trying to avoid at this stage of the "fix".

From what i've gathered, i want to have genisoimage and wodim off my system until after i've downloaded cdrecord and mkisofs and been able to temporarily rename them so as to circumvent wodim and genisoimage's search and destroy function.  problem is that apt-get doesn't want to let me install cdrecord and mkisofs because wodim and genisoimage aren't there.  If I try to install cdrecord and mkisofs without removing the other two from my system, then apt-get just selects the other two for reinstallation anyways.  So I'm stuck in a Catch-22 right now.

---

### Post by matrixblue on 2009-07-12
Try a regular sudo apt-get remove wodim genisoimage

It'll remove all of your burning programs but you can reinstall them before the final rename

---

### Post by Jiawen on 2009-08-09
What do we do if we're still using 7.10? K3B, Brasero and the other burning programs sometimes work for me, but far too little. I just ended up with a pile of coasters trying to get even one to burn correctly. 

Please help!

---


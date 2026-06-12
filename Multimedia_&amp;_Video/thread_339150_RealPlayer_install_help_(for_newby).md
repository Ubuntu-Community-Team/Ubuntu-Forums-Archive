---
title: "RealPlayer install help (for newby)"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by dmj99 on 2007-01-15
I want to install RealPlayer (Ubuntu 6.10).  I downloaded the file from RealPlayer.  It's in my home folder.  Here is what's happening:

don@AMD-desktop:~$ ls
Desktop  Examples  RealPlayer10GOLD.bin
don@AMD-desktop:~$ dir -l
total 5684
drwxr-xr-x 2 don don    4096 2007-01-15 09:06 Desktop
lrwxrwxrwx 1 don don      26 2007-01-14 09:48 Examples -> /usr/share/example-content
-rwxr-xr-x 1 don don 5802563 2007-01-14 21:16 RealPlayer10GOLD.bin
don@AMD-desktop:~$ ls *bin
RealPlayer10GOLD.bin
don@AMD-desktop:~$ sudo chmod a+x RealPlayer10GOLD.bin
Password:
don@AMD-desktop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory

Am I doing something wrong?  Thank you for your help,

Don :(

---

### Post by ajgreeny on 2007-01-15
I'm pretty sure it's in the repos so make sure you have the universe and multiverse repos activated and you should find it.  For more details look here:-
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

---

### Post by dmj99 on 2007-01-15
Thanks for your reply.  Using apt-get or synaptic package manger doesn't seem to work for me.  I have tried changing the sources.lst file to include all repo's suggested in the Edgy guide for  RealPlayer. . . that's why I was trying to install the binary directly.  But this didn't seem to work for me either.  

Regards,

Don

---

### Post by obsidion on 2007-01-15
> **dmj99 said:**
> I want to install RealPlayer (Ubuntu 6.10).  I downloaded the file from RealPlayer.  It's in my home folder.  Here is what's happening:

don@AMD-desktop:~$ ls
Desktop  Examples  RealPlayer10GOLD.bin
don@AMD-desktop:~$ dir -l
total 5684
drwxr-xr-x 2 don don    4096 2007-01-15 09:06 Desktop
lrwxrwxrwx 1 don don      26 2007-01-14 09:48 Examples -> /usr/share/example-content
-rwxr-xr-x 1 don don 5802563 2007-01-14 21:16 RealPlayer10GOLD.bin
don@AMD-desktop:~$ ls *bin
RealPlayer10GOLD.bin
don@AMD-desktop:~$ sudo chmod a+x RealPlayer10GOLD.bin
Password:
don@AMD-desktop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory

Am I doing something wrong?  Thank you for your help,

Don :(



   There are instructions on the realplayer site..

 However cd Desktop

chmod a+x RealPlayer10GOLD.bin

This makes it an executable file

sudo ./RealPlayer10GOLD.bin

This installs system wide, it will ask you questions about where you want it etc, pay attention to those as depending on your browser you may need to install the plugins later.

---

### Post by dmj99 on 2007-01-16
Here is what's going on:

don@AMD-desktop:~$ ls
Desktop  Examples  RealPlayer10GOLD.bin
don@AMD-desktop:~$ chmod a+x RealPlayer10GOLD.bin
don@AMD-desktop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
don@AMD-desktop:~$ 


The Real Player binary is in my home directory.  It is already executable.  

don@AMD-desktop:~$ ls
Desktop  Examples  RealPlayer10GOLD.bin
don@AMD-desktop:~$ sudo chmod a+x RealPlayer10GOLD.bin
don@AMD-desktop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
don@AMD-desktop:~$ 

Something is still wrong.  Any idea?

---

### Post by obsidion on 2007-01-16
try ls -s to see how big the bin file is

Mine is 5680k

Also after you chmod a+x 'd it did it change to green to insdicate it was now runnable ?

---

### Post by dmj99 on 2007-01-16
The file RealPlayer10GOLD.bin is green both before and after the chmod command.

Don

---

### Post by dmj99 on 2007-01-16
don@AMD-desktop:~$ dir *bin -l
-rwxr-xr-x 1 don don 5802563 2007-01-14 21:16 RealPlayer10GOLD.bin

The file is 5802563

---

### Post by obsidion on 2007-01-16
> **dmj99 said:**
> don@AMD-desktop:~$ dir *bin -l
-rwxr-xr-x 1 don don 5802563 2007-01-14 21:16 RealPlayer10GOLD.bin

The file is 5802563

  Got me beat in the several times I have installed Real I have never had this happen to me.

one thing that just may work, apparently dash is the default now rather than bash
so try sudo bash

and then try again, I have my doubts but it is worth a go

exit to get out of there

Failing that and maybe anyway add this to your sources.list
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

 It has realplayer and opera there.

---

### Post by dmj99 on 2007-01-16
Thank you for trying to help me with this.  I tried the sudo bash ./RealPlayer10GOLD.bin command with no result.  The site: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main  is in my sources list.  Searches for realplayer kept coming up empty. . .that's why I was trying to install the binary directly.  

Anyway. . . I appreciate your time and interest,

Don ;)

---

### Post by pickarooney on 2007-01-16
sudo sh ./RealPlayer10GOLD.bin

---

### Post by obsidion on 2007-01-16
> **dmj99 said:**
> Thank you for trying to help me with this.  I tried the sudo bash ./RealPlayer10GOLD.bin command with no result.  The site: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main  is in my sources list.  Searches for realplayer kept coming up empty. . .that's why I was trying to install the binary directly.  

Anyway. . . I appreciate your time and interest,

Don ;)

  I cannot see why, I just added it to my list, as I wasn't using it before. 
Ran the update and then opened synaptic to check and there it was.

you diid sudo apt-get update after adding the line to the sources.list didn't you ?
I hope you did the suggested bash operation in seperate lines.

ie sudo bash
then

./Real etc   btw try using tab to autocomplete ie ./Re then hit tab maybe the name has a space or something

---

### Post by drs305 on 2007-01-16
Do you have Automatix2 on your system. I used it last week and am pretty sure that's how I installed RealPlayer  10. You might try it  ([www.getautomatix.com)](www.getautomatix.com)). It also easily installs other nice programs for us newbies - Wine, Thunderbird, sun-java-jre-1.5, etc.

---

### Post by david_2001 on 2007-01-16
Realplayer isn't in the edgy-commercial repository but the dapper version works on edgy, so the correct sources.list entry will be:
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by obsidion on 2007-01-16
> **david_2001 said:**
> Realplayer isn't in the edgy-commercial repository but the dapper version works on edgy, so the correct sources.list entry will be:


  It is in the repos I use.


from a printout of the edgy indices

realplay	optional	graphics	
desktopsecure	optional	misc	
opera	optional	web	

Maybe it has been added since you last looked and wasn't there when you first installed edgy.

---

### Post by dmj99 on 2007-01-16
Thank you all for your help.  At this point, I think I'm going to move on.  I will try automatix2 to see if that helps.  

Regards,

Don

---

### Post by david_2001 on 2007-01-17
> **obsidion said:**
> It is in the repos I use.


from a printout of the edgy indices

realplay	optional	graphics	
desktopsecure	optional	misc	
opera	optional	web	

Maybe it has been added since you last looked and wasn't there when you first installed edgy.

Curious, the entire contents of [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.gz) is as follows:

> Package: opera
Priority: optional
Section: web
Installed-Size: 12560
Maintainer: Opera Packaging Team <packager@opera.com>
Architecture: i386
Version: 9.10-20061214.6ubuntu2
Replaces: opera-static
Provides: opera-static, www-browser
Depends: libc6 (>= 2.4-1), libgcc1 (>= 1:4.1.1-12), libice6, libqt3-mt (>= 3:3.3.6), libsm6, libstdc++6 (>= 4.1.1-12), libx11-6, libxext6, libxt6, zlib1g (>= 1:1.2.1)
Recommends: libaspell15
Suggests: flashplugin-nonfree | libflash-mozplugin
Conflicts: opera-static
Filename: pool/main/o/opera/opera_9.10-20061214.6ubuntu2_i386.deb
Size: 5559256
MD5sum: 62483694d5d73791e2c29e0dba01e1bb
Description: The Opera Web Browser
 Welcome to the Opera Web browser. It is smaller, faster,
 customizable, powerful, yet user-friendly. Opera eliminates
 sluggish performance, HTML standard violations, desktop
 domination, and instability. This robust Web browser lets you
 navigate the Web at incredible speed and offers you the best
 Internet experience.
 The binaries were built on Debian using gcc-4.0.0.

If I just have edgy-commercial in my sources.list then no realplayer.  My guess would be that you are getting realplayer from another repository.

---

### Post by raimennendez on 2007-01-17
hi,
my source.list:
```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://it.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://it.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://it.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com edgy-commercial main 
deb-src http://archive.canonical.com edgy-commercial main

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://it.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://it.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

deb-src http://it.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ax.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://ax.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```

then I try to install realplayer:

```
$ sudo apt-get install realplayer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate
```

way that?
rai

---

### Post by david_2001 on 2007-01-17
This is mine.  It's not complicated but gets you realplayer if you want it, plus some other useful extras:

> # Ubuntu Main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse

# Bug fix Updates
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

# kubuntu.org packages for the latest KDE version
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main

# Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

# Backports Repository
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# Canonical Commercial Repository (Opera,Real Player10.. etc)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# Sevea&#8217;s Repository (Multimedia Packages)
deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all
deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all

# Wine HQ
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by raimennendez on 2007-01-17
hi,
thanks for the repply but:


> 
W: GPG error: [http://kubuntu.org](http://kubuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: You may want to run apt-get update to correct these problems


and then:
> 
~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


Maybe I must validate the keys of the repository? That:

```
wget -q http://seveas.imbrandon.com-key.gpg -O- | sudo apt-key add -
```

it's right?
than you
bye
rai

---

### Post by david_2001 on 2007-01-18
The package name is actually realplay, so
```
sudo apt-get install realplay
```
is what you need to use.

---

### Post by Turtle.net on 2007-01-20
> **obsidion said:**
> 

Failing that and maybe anyway add this to your sources.list
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

 It has realplayer and opera there.
It seems that this repo does not have realplayer anymore, but only opera ...

But you can find the .deb in [http://archive.canonical.com/ubuntu/pool/main/r/realplay/](http://archive.canonical.com/ubuntu/pool/main/r/realplay/)

---

### Post by Tominator on 2007-02-07
Realplayer.com insists that you start at their website. You cannot get a full install from universe or multiverse or both combined.

---

### Post by Turtle.net on 2007-02-08
Using the link in my previous post I was able to install directly the deb with gdebi and without going to realplayer's website (if my memory doesn't betray me)

---

### Post by aldin on 2007-03-08
hi, just to add, i have ubuntu-6.10 i386 & amd64 arch, on my i386 ubuntu installation

./RealPlayer10GOLD.bin (works just fine)

but when i try to do the same on amd64 it says:

aldin@localhost64:~/Desktop$ ./RealPlayer10GOLD.bin 
bash: ./RealPlayer10GOLD.bin: No such file or directory
aldin@localhost64:~/Desktop$

ps:
both had +x (777) so i think its only problem if u have amd64 and trying to extract official real.com's realplayer package...

---

### Post by object16 on 2007-03-08
I find the best site to explain how to install real player, and lots of other useful stuff
was written by someone from Cornell:
site adress =
[http://www.cs.cornell.edu/~djm/ubuntu/#multimedia](http://www.cs.cornell.edu/~djm/ubuntu/#multimedia)
Just cut and paste into the terminal.

---

### Post by ikjldsa on 2007-03-12
Put the bin file in your desktop first
Try the following in the terminal:

chmod a+x /home/(username?????)/Desktop/RealPlayer10GOLD.bin 

/home/(username?)/Desktop/RealPlayer10GOLD.bin 

It should start installin g in the terminal afterward.

---


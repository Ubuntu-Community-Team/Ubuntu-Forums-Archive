---
title: "HandBrake Compile Error in Hardy 8.04"
date: 2008-06-22
forum: Multimedia Software
---

### Post by Neon Lemmy Koopa on 2008-06-22
[FONT=Verdana]Ok heres the thing.  I checked out the source for HandBrake from the SVN repository.  I followed the instructions on the website.  I ran jam and everything started to go.  It was downloading and compiling some dependencies.  Now for the problem.  I was following the terminal text.  I kept noticing it said "...failed <dependency>"  It didnt compile correctly.  When some of these failed, others failed because of dependencies.  After it was done...well heres the last few lines in the terminal.

[/FONT]```
...failed updating 39 target(s)...
...skipped 6 target(s)...

```I had an active connection, and I even went into apt and installed the dependencies my own self, but nothing worked.

PS if I posted in the wrong section, please dont shoot me.

---

### Post by cozmicharlie on 2008-06-22
There is a good list of the dependencies on this thread maybe this will help [http://ubuntuforums.org/showthread.php?t=835825&highlight=handbrake](http://ubuntuforums.org/showthread.php?t=835825&highlight=handbrake)


## QUICK SETUP GUIDE FOR HANDBRAKECLI LATEST SVN ON UBUNTU
## ------------------------------------------------------------

1) Add the Medibuntu repositories

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup && sudo nano /etc/apt/sources.list

************************************************** **********************************

## +++ Medibuntu +++
## Packages that can't be included in Ubuntu for legal reasons
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

************************************************** **********************************

( ^ copy'n'paste into source list )

wget [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

2) Install dependencies for building (very poorly docuemented, but I've managed to
coble together a working list) and build (jam can take awhile, but it's their
reccomended method). I keep my stuff in my home folder so cd there.

sudo apt-get update && sudo apt-get install automake build-essential jam libdvdcss2-dev libtool subversion yasm zlib1g-dev libbz2-dev dvdbackup xmlto texinfo g77 gfortran libgtk2.0-dev nasm doxygen libsdl1.2-dev gfortran-multilib gcc-multilib g++-multilib libesd0-dev libgtk1.2-dev libfftw3-dev electric-fence && svn co svn://svn.handbrake.fr/HandBrake/trunk hb-dev && cd hb-dev && ./configure && jam

---

### Post by Neon Lemmy Koopa on 2008-06-22
That helped.  I managed to get it installed.  Thank you very much

---


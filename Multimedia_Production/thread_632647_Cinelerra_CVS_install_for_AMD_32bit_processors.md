---
title: "Cinelerra CVS install for AMD 32bit processors"
date: 2007-12-05
forum: Multimedia Production
---

### Post by fsman on 2007-12-05
Looks like the standard repos don't aren't complied to run with AMD 32bit processors. Running cinelerra will gave a "core dump" error.

However, someone has created a repo for AMD32 bit and posted on the Cinelerra mailing list.

Here is what I added - all working fine now

You can found cinelerra that work on amd k7 for ubuntu on my repository.
You mast remove old cinelerra repository and repleace with this

Add the following repos for /etc/apt/sources.list
deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main
deb-src [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main

then
wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key
add -
sudo apt-get update
sudo apt-get remove cinelerra libmpeg3hv libquicktimehv libguicast # if
cinelerra already installed
sudo apt-get install cinelerra

thats all

thanks to Paolo Rampino aka Akirad

---

### Post by rsambuca on 2007-12-05
> **fsman said:**
> Looks like the standard repos don't aren't complied to run with AMD 32bit processors. Running cinelerra will gave a "core dump" error.


Cinelerra isn't in the Ubuntu repos at all, let alone cpu specific versions.

---

### Post by fsman on 2007-12-06
When i said standard repo i should have been clearer.
The "community cinelerra" team have repos for ubuntu here [http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)
it was these that I was referering too as "standard". i.e. standard from the cinelerra team.

However, these don't seem to work for AMD 32bit processors. They are compliled for AMD64 i386 etc. Their mailing lists have some threads which recognise the problem.

now they  have a new repo with for those who want to install cinelerra on their AMD 32bit machines. - i.e. my original post.

hope this clears it up - and all people to install cinelerra using the "community cinelerra" packages.

---

### Post by tomtiger on 2007-12-20
I tried to install cinelerra on ubuntu 7.10 but it doesn't work. 

Here is what synaptic told me: 

depends on: »libquicktimehv-k8«, but it don't will be installed.
depends on: »ffmpeg«, but it don't will be installed.

after installing Libquicktimehv-k8: 


cinelerra-k8:
depends on: »ffmpeg«, but it don't will be installed.

ffmpeg:
depends on: »libavcodeccvs51«, abut it don't will be installed.
depends on: »libavformatcvs51«, abbut it don't will be installed.

depends on: »libfaad0«, but it don't will be installed.

when I try to install libfaad0 I get the message: 
Packets to be deleted: 
libfaad2-0
Libquicktimehv-k8

It seems that cinelerra needs libfaad2-0 for Libquicktimehv-k8 and libfaad0 for ffmpeg at the same time and this is not possible. I get the same with the other versions of cinelerra (generic and k-7). Do you have a solution?


thanks, 

Thomas

---

### Post by rsambuca on 2007-12-20
> **tomtiger said:**
> I tried to install cinelerra on ubuntu 7.10 but it doesn't work. 

Here is what synaptic told me: 

depends on: »libquicktimehv-k8«, but it don't will be installed.
depends on: »ffmpeg«, but it don't will be installed.

after installing Libquicktimehv-k8: 


cinelerra-k8:
depends on: »ffmpeg«, but it don't will be installed.

ffmpeg:
depends on: »libavcodeccvs51«, abut it don't will be installed.
depends on: »libavformatcvs51«, abbut it don't will be installed.

depends on: »libfaad0«, but it don't will be installed.

when I try to install libfaad0 I get the message: 
Packets to be deleted: 
libfaad2-0
Libquicktimehv-k8

It seems that cinelerra needs libfaad2-0 for Libquicktimehv-k8 and libfaad0 for ffmpeg at the same time and this is not possible. I get the same with the other versions of cinelerra (generic and k-7). Do you have a solution?


thanks, 

Thomas

Do you have all of your repositories enabled?  Go to "System - Administration - Software Sources".  Make sure all of the boxes are checked.  Close the Window and select upgrade sources when prompted.  Then try installing again.

---

### Post by tomtiger on 2007-12-21
Yes, all the sources needed are enabled.  Here is my "sources.list"

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-propert
ies

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software
-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://giss.tv/~vale/ubuntu32 ./
deb http://www.debian-multimedia.org testing main
# deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 NETINST Binary-1 20070820-20:21]/ etch contrib main
deb http://repository.akirad.net akirad-gutsy main
deb-src http://repository.akirad.net akirad-gutsy main
# deb http://www.kiberpipa.org/~minmax/cinelerra/builds/athlonxp/ ./
(END)
```

Thomas

---

### Post by fsman on 2007-12-21
Hum - on the surface your repos look ok.

the packagers now has a homepage. [http://repository.akirad.net/](http://repository.akirad.net/)

I suggest you clean up your repo. and follow his instructions.

It seems strange that ffmpeg isn't installed.

Are you selecting the right version of cinelerra for your CPU?

---

### Post by tomtiger on 2007-12-23
Hallo, 
Yes I think I 've choosen the right Version for my cpu. Here is what dmesg told me:

```
stern@Inga-kiste:~$ sudo dmesg |grep -i cpu
[    0.000000] Initializing CPU#0
[   32.673380] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   32.753538] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   32.753550] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.753553] CPU: L2 Cache: 512K (64 bytes/line)
[   32.753557] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   33.163052] CPU0: AMD Athlon(tm) XP 2100+ stepping 00
[   33.308551] Brought up 1 CPUs
[   33.879673] Switched to high resolution mode on CPU 0
stern@Inga-kiste:~$ 

```
To be sure I tried all versions of cinelerra. The result stays the same. 
How do I clean up the repo?

Thanks

Thomas

---

### Post by akir4d on 2007-12-28
you must remove debian multimedia!
Also need to come back to ubuntu package:

- open synaptic
- reload 
- filter by local or obsolete package
- remove ffmpegcvs
- with ctrl+e revert libavcodec libavformat libpostproc libfaad and libfaac to ubuntu version
- now you can install cinelerra

visit [http://repository.akirad.net]("http://repository.akirad.net") for all news

Byez

Paolo Rampino aka Akirad

---


---
title: "Package vlc has no installation candidate"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by linuxvacuum on 2008-01-04
I cannot get vlc to work :mad:, I tried :
> sudo apt-get purge vlc
sudo apt-get install vlc


Then I get :
> Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libvlc1 vlc-nox libvlc0
E: Package vlc has no installation candidate



What can I try now?
I am using Ubuntu 7.10.

---

### Post by taurus on 2008-01-04
Sounds to me like you don't have any repos or limited number of repos available in /etc/apt/sources.list.  Therefore, you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  Now, run

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by linuxvacuum on 2008-01-04
Ok I tried what you recommended and I get the exact same error message! This is weird, I thought the purge command removed everything related to the program.

---

### Post by taurus on 2008-01-04
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by mc4man on 2008-01-04
Did you happen  to compile/ install or try to compile/ install a ver. of vlc from svn repo ?

---

### Post by linuxvacuum on 2008-01-05
Yes and here is my /etc/apt/sources.list

> # deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb file:/media/iso/ gutsy main restricted
 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-updates main restricted universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy multiverse universe main restricted
deb [http://gulus.USherbrooke.ca/ubuntu/](http://gulus.USherbrooke.ca/ubuntu/) gutsy-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties


#Innotek repos or VirtualBox
 deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free


#VLC
deb [http://nightlies.videolan.org/build/gutsy-i386/arch](http://nightlies.videolan.org/build/gutsy-i386/arch) ./

---

### Post by taurus on 2008-01-05
Did you remember to run **sudo apt-get update** first?

I guess you want the latest version of vlc (last repo in /etc/apt/sources.list)!

---

### Post by linuxvacuum on 2008-01-05
I sure tried it and the same error is there.

---

### Post by taurus on 2008-01-05
What if you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the last line to comment it out for now.

```
#deb http://nightlies.videolan.org/build/gutsy-i386/arch ./
```
Save it.  Then, run

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by linuxvacuum on 2008-01-05
If I leave the cdrom as the only repository, I get the following

sudo apt-get update
> Ign file: gutsy/main Translation-en_CA
Ign file: gutsy/restricted Translation-en_CA
Get:1 file: gutsy Release.gpg [189B]
Get:2 file: gutsy Release [1757B]
Ign file: gutsy/main Packages
Ign file: gutsy/restricted Packages
Reading package lists... Done

sudo apt-get install vlc
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
**Package vlc is not available, but is referred to by another package.**
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libvlc1
E: Package vlc has no installation candidate

I can't do much with only that error message...

---

### Post by taurus on 2008-01-05
Comment out by placing a # in front of the first line and the last line.  Then, _remove_ the # from all the lines that start with deb & deb-src.  Save it and then run

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by linuxvacuum on 2008-01-05
Nope, nothing.

---

### Post by taurus on 2008-01-05
Can you post your /etc/apt/sources.list again.

```
cat /etc/apt/sources.list
```
Also, the complete outputs of these two commands.

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by linuxvacuum on 2008-01-05
Every listing is in page 1 of this post.

---

### Post by mc4man on 2008-01-05
that was the worst choice for trying the latest ver. of vlc, very unstable and really meant for bug testing. Next time (if ever ) get a tarball and compile or checkout the latest trunk and compile.
i've done both and it's very easy to remove.
 look in synaptic for libvlc1  and remove it

edit: removing libvlc1 and by extension vlc-nox will do the trick, do comment out the nightly build source when going to install the current repo ver.
actually it's a very quick and easy way to try the latest ver. though it does warn about being unstable. I have on 1 box an install from the tarball that runs fine

---

### Post by linuxvacuum on 2008-01-05
Ok I removed libvlc1 with synaptic, but I cannot remove vlc-nox and I still get the same error message, :-({|=

---

### Post by mc4man on 2008-01-06
I might be missing something ,i'm pretty new to linux, but the only time I've seen you can't remove something is when it's not there.(or you don't have permissions)  I did what I think you did and it's very straightforward to remove the nightly - vlc 0.9.0..... and install the repo 0.8.6. Go to system>administration>software sources and under third party make sure the nightlies ... is unchecked. In synaptic search vlc and check status of vlc, vlc-nox, libvlc0 and libvlc1. If need be remove them all.(only 3 out of 4 possible )  What you want is vlc 0.8.6, vlc-nox 0.8.6 and libvlc0 0.8.6

---

### Post by buccaneere on 2008-01-06
I got VLC to install with:

[HTML]sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc[/HTML]

Before that, it returned 'couldn't find VLC. I went to System > Administration >software sources > main tab > check all sources.

Got installed, but still no joy with playin' files..........

---

### Post by linuxvacuum on 2008-01-06
Using Synaptic, I can only install libvlc0 and vlc-nox. After that when I launch vlc from the command line, it loads a file but I get no video output! I don't want this, what I need is the graphical version like I had before. I am really stuck here! ](*,)

---

### Post by mc4man on 2008-01-06
go back into Synaptic, search vlc and what is shown for vlc? ie. ver., , installed - green box , not installed - blank box,  installed with update avail. - green with arrow
odds are it a blank box for version 0.8.6, then go ahead and check vlc and install it

---

### Post by linuxvacuum on 2008-01-06
Yes I already tried many times these simple solutions. My vlc in synaptic has no version and if I check if it says the same kind of error "depends on other packages" that I mentionned earlier. I hope someone can tell me the more elaborate command line commands to fix this.

---

### Post by linuxvacuum on 2008-01-08
bump

---

### Post by mc4man on 2008-01-08
If no additional help/resolution is forthcoming it would be interesting to see the results of a file search of vlc.  Highlight all the entries, r click, save results as text file and post. It would help show what you did to install and what remains and where

---

### Post by linuxvacuum on 2008-01-08
What do I type in the terminal for that? The option isn't in Synaptic

---

### Post by mc4man on 2008-01-08
Go to (upper task bar) Places> Search for files - type in vlc. Highlight 1st. file, go down to last file and shift/ r. click> save results as. Gve it a name and a text file will be saved in your home folder.
edit:switch the look in to file system

---

### Post by linuxvacuum on 2008-01-13
OS REINSTALLED :evil:

---


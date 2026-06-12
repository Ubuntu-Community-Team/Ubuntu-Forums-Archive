---
title: "Banshee unmet dependencies"
date: 2009-10-19
forum: Multimedia Software
---

### Post by motorhead_1 on 2009-10-19
Hi, I've tried to install Banshee but something went wrong, at the moment I've  a permanent 'error' symbol in my task bar, due to this it's impossbile to perform a full update of the packages.
Trying again to install Banshee from the command line I've the following:

The following packages have unmet dependencies:
  banshee: Depends: libgconf2.24-cil (>= 2.24.0) but it is not going to be installed
           Recommends: podsleuth (>= 0.6.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

How do I cope with this? thanks!

---

### Post by vinutux on 2009-10-19
Which version of ubuntu u r using ?

Anyway type this ```
sudo apt-get install banshee
``` in terminal (Applications > Accessories > Termianl)

---

### Post by motorhead_1 on 2009-10-19
> **vinutux said:**
> Which version of ubuntu u r using ?

Anyway type this ```
sudo apt-get install banshee
``` in terminal (Applications > Accessories > Termianl)
yea that's what I did and in response I've this: The following packages have unmet dependencies:
  banshee: Depends: libgconf2.24-cil (>= 2.24.0) but it is not going to be installed
           Recommends: podsleuth (>= 0.6.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

actually I've noticed that the program has been installed since I'm using it right now, I just wanted to fix these unmet dependencies

---

### Post by vinutux on 2009-10-19
> **motorhead_1 said:**
> yea that's what I did and in response I've this: The following packages have unmet dependencies:
  banshee: Depends: libgconf2.24-cil (>= 2.24.0) but it is not going to be installed
           Recommends: podsleuth (>= 0.6.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

actually I've noticed that the program has been installed since I'm using it right now, I just wanted to fix these unmet dependencies

System > Administration > Synaptic in settings menu > software source in third party software tab disable everything.....

Realod synaptic try install now .........

---

### Post by motorhead_1 on 2009-10-19
> **vinutux said:**
> System > Administration > Synaptic in settings menu > software source in third party software tab disable everything.....

Realod synaptic try install now .........
I've removed the damged package through synaptic package manager, however banshee too is now uninstalled.
I cannot find 'software source in third party' , is it under settings in synaptic package manager??  do you mind posting a screen please? I'm a completely newbie

---

### Post by vinutux on 2009-10-19
Sorry.......System > Administration > Synaptic in settings menu > [COLOR="Red"]Repositries (also called softwaresources)[/COLOR] 

On third party software tab Disable everything........
Then reload synaptic (Reload button top)

Then install banshee from there (search with serach box or just type banshee...> right click mark for installation > Applay (applay button top bar))

---

### Post by motorhead_1 on 2009-10-19
"Could not mark all packages for installation or upgrade:

Package banshee has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"

---

### Post by vinutux on 2009-10-19
Wich version of ubuntu U R using and check there is not broken pakages in synaptic sections (sidebar)

---

### Post by motorhead_1 on 2009-10-19
no broken packages at the moment. running ubuntu 9.04

---

### Post by vinutux on 2009-10-19
What  ? ok

Try this tooooo

In terminal ```
sudo apt-get install -f banshee
```

Its force command...(generally not recommended)

---

### Post by vinutux on 2009-10-19
Are u installing/combiling/building anything from source files(tar.gz)....?

Any way loo late to sleep for me....bye... see u in morning...:)

---

### Post by motorhead_1 on 2009-10-19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  banshee: Depends: libgconf2.24-cil (>= 2.24.0) but it is not going to be installed
E: Broken packages

---

### Post by motorhead_1 on 2009-10-19
> **vinutux said:**
> Are u installing/combiling/building anything from source files(tar.gz)....?


I've no idea :(

---

### Post by mc4man on 2009-10-19
maybe run this and post to see if your sources are ok
```
cat /etc/apt/sources.list
```

---

### Post by vinutux on 2009-10-20
> **motorhead_1 said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  banshee: Depends: libgconf2.24-cil (>= 2.24.0) but it is not going to be installed
E: Broken packages

That shows you have broken pakags in synaptic Edit menu > Fix brocken pakages...........

---

### Post by motorhead_1 on 2009-10-20
> **mc4man said:**
> maybe run this and post to see if your sources are ok
```
cat /etc/apt/sources.list
``````
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty multiverse
# deb http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main # xorg
deb http://cz.archive.ubuntu.com/ubuntu karmic main
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main

```

> **vinutux said:**
> That shows you have broken pakags in synaptic Edit menu > Fix brocken pakages...........
ok, done.

---

### Post by motorhead_1 on 2009-10-20
this what happens if I try to install it from synaptic p.m.

[[IMG]http://img44.imageshack.us/img44/2668/screenshot1xs.th.png[/IMG]]("http://img44.imageshack.us/i/screenshot1xs.png/")

[[IMG]http://img132.imageshack.us/img132/35/screenshot2vs.th.png[/IMG]](http://img132.imageshack.us/i/screenshot2vs.png/)

---

### Post by vinutux on 2009-10-20
> **motorhead_1 said:**
> ```
# 
.......

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
[COLOR="Red"][B]deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main # xorg
deb http://cz.archive.ubuntu.com/ubuntu karmic main
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main[/B][/COLOR]

```

Listen carefully and plz....do exactly what is here described

There is Three third party ppa sources in your source.list

OK one of them is from banshee team.... plz disable other two sources in synaptic or delete those two sources from source.list and save it

Synaptic > setting menu > repositories > Third party Software tab Disable those two sources (cz.archive and edgers/ppa)

Reload synaptic and install banshee........

---

### Post by motorhead_1 on 2009-10-20
> **vinutux said:**
> Listen carefully and plz....do exactly what is here described

There is Three third party ppa sources in your source.list

OK one of them is from banshee team.... plz disable other two sources in synaptic or delete those two sources from source.list and save it

Synaptic > setting menu > repositories > Third party Software tab Disable those two sources (cz.archive and edgers/ppa)

Reload synaptic and install banshee........
I've deleted those two sources from source.list 
(sudo gedit /etc/apt/sources.list)  then I saved it 
```

#
.
.
.
.
.
.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main

```then tried to install banshee from synaptic and I get the same errors

[[IMG]http://img44.imageshack.us/img44/2668/screenshot1xs.th.png[/IMG]]("http://img44.imageshack.us/i/screenshot1xs.png/")

[[IMG]http://img132.imageshack.us/img132/35/screenshot2vs.th.png[/IMG]]("http://img132.imageshack.us/i/screenshot2vs.png/")

---

### Post by vinutux on 2009-10-20
Ok that means you are installed some peace of packages from that third party/deleted ppas....those packages have a conflict with banshee package .....means both packageshave almost same libs or so....... if you really want to install banshee you must uninstall  those packages from that two repos you are already installed in U R system.....

---

### Post by motorhead_1 on 2009-10-20
> **vinutux said:**
> Ok that means you are installed some peace of packages from that third party/deleted ppas....those packages have a conflict with banshee package .....means both packageshave almost same libs or so....... if you really want to install banshee you must uninstall  those packages from that two repos you are already installed in U R system.....
how do I know which packages are to be removed and how do I do this? :oops::D

---

### Post by motorhead_1 on 2009-10-20
I've installed podsleuth  and I was about to install  libgconf2.24-cil  taken from banshee's official site but I've got the following:
[COLOR=Red]Error: Breaks exisiting package 'libgconf2.0-cil' conflict: libgconf2.24-cil ( )

[COLOR=Black]edit, just removed it

```
sudo apt-get remove libgconf2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 libmono-zeroconf1.0-cil libart2.0-cil libflickrnet2.2-cil
  libtaglib2.0-cil libboo2.0-cil libavahi1.0-cil libgnome-vfs2.0-cil
  libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libgconf2.0-cil libgnome2.24-cil
0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
After this operation, 1,036kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 168746 files and directories currently installed.)
Removing libgnome2.24-cil ...
Removing libgnome2.24-cil from Mono
Removing libgconf2.0-cil ...
Removing libgconf2.0-cil from Mono

```
[/COLOR][/COLOR][COLOR=Red] [/COLOR]

---

### Post by motorhead_1 on 2009-10-20
Problem solved now, everything it's fine ;)

[[IMG]http://img10.imageshack.us/img10/4989/screenshot3hm.th.png[/IMG]](http://img10.imageshack.us/i/screenshot3hm.png/)

---

### Post by vinutux on 2009-10-20
mmm.... and plz share a bit info about HOW TO SOLVED THIS for future references. and it helps people who suffer similar problems....:)

---

### Post by directhex on 2009-10-20
The problem is caused by trying to use Jaunty Banshee packages on Karmic.

---

### Post by motorhead_1 on 2009-10-20
> **vinutux said:**
> mmm.... and plz share a bit info about HOW TO SOLVED THIS for future references. and it helps people who suffer similar problems....:)
this was the problem [COLOR=Red]Error: Breaks exisiting package 'libgconf2.0-cil' conflict: libgconf2.24-cil ( )  ;) [COLOR=Black]i've removed the first package then the installtion was completed[/COLOR]
[/COLOR]

---

### Post by directhex on 2009-10-20
> **motorhead_1 said:**
> this was the problem [COLOR=Red]Error: Breaks exisiting package 'libgconf2.0-cil' conflict: libgconf2.24-cil ( )  ;) [COLOR=Black]i've removed the first package then the installtion was completed[/COLOR]
[/COLOR]

The problem is what I said it is.

Your solution works around the issue by forcing the Jaunty version of GConf# to be installed instead of the Karmic version, which will prevent Karmic versions of apps like Tomboy and F-Spot from being installed

---

### Post by mc4man on 2009-10-20
> The problem is.... (was

Review his sources.list carefully and you will see what the problem was

(noting he is running 9.04, and had a karmic main repo enabled

---

### Post by directhex on 2009-10-20
> **mc4man said:**
> (noting he is running 9.04, and had a karmic main repo enabled

At which point it's impossible to say with any certainty that he's running 9.04 - as any number of packages may have been updated to 9.10 versions

---

### Post by motorhead_1 on 2009-10-21
> **motorhead_1 said:**
> no broken packages at the moment. running ubuntu 9.04
;)

---


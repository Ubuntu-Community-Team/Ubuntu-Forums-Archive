---
title: "received error message this am"
date: 2011-03-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-03-04
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

---

### Post by rburkartjo on 2011-03-04
also noted that now a broken packages icon appears in the top menu bar

---

### Post by dino99 on 2011-03-04
clean the sources:

sudo rm /var/cache/apt/archives/*

then update upgrade again

---

### Post by rburkartjo on 2011-03-04
dino got this error message


ray@ray-desktop:~$ sudo rm /var/cache/apt/archives/*
[sudo] password for ray: 
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
ray@ray-desktop:~$

---

### Post by Framli on 2011-03-04
sudo rm **-rf** /var/cache/apt/archives/*
:)

---

### Post by rburkartjo on 2011-03-04
fra tks did what you said but still get icon showing broken packages that werent installed

---

### Post by Harry33 on 2011-03-04
> **rburkartjo said:**
> fra tks did what you said but still get icon showing broken packages that werent installed

Open Synaptic. It will show what is wrong.
Print here the error message (the broken packages).

---

### Post by dino99 on 2011-03-04
> **rburkartjo said:**
> fra tks did what you said but still get icon showing broken packages that werent installed

Hey, i've never said to remove /partial

this subfolder is needed, you might recreate it. Then try to understand what a command do, instead of following scary post.

---

### Post by rburkartjo on 2011-03-04
dino good point. if i open the spm it shows no broken packages. if i boot up in the recovery mode and try to fix broken packages. the broken icon still appears when i boot up into the the desktop. i wonder if this is just going to be a feature in 11.04 that indicates that you have some broken packages that wont be installed until all the dependentcies have been resolved

---

### Post by Framli on 2011-03-04
I apologize for my silly mistake, I'm used to aptitude instead of apt-get, and it automatically creates partial/ if missing.

---

### Post by dino99 on 2011-03-04
> **rburkartjo said:**
> dino good point. if i open the spm it shows no broken packages. if i boot up in the recovery mode and try to fix broken packages. the broken icon still appears when i boot up into the the desktop. i wonder if this is just going to be a feature in 11.04 that indicates that you have some broken packages that wont be installed until all the dependentcies have been resolved

i dont get this warning, but i often (at least once a week) clean the room with bleachbit & gconf-cleaner

you can run:

sudo dpkg --configure -a

sidenote: both apt-get & aptitude makes the same job (roughly) but have each their own way, that mean they build their own database in a different way. So choose to use either apt-get (more bug free) or aptitude, but dont mix them as that conflict sometimes.

---

### Post by rburkartjo on 2011-03-04
tks dino will give that a try

---

### Post by rburkartjo on 2011-03-04
dino i tried that before but ran them again as you suggested. still the same. no big deal. as i noted before maybe just a new feature of 11.04.

---

### Post by plucky on 2011-03-05
I had this problem caused by libcanberra-gtk3-0 & libcanberra-gtk3-module not installing causing libcanberra-gtk0  not to upgrade.

Open Synaptic Package Manager and navigate to **Status > Not Installed** and see what is there.I had to mark libcanberra-gtk3-0 & libcanberra-gtk3-module to be upgraded first and after that was upgraded it would then upgrade libcanberra-gtk0.

The indicator in the panel then disappeared.

See if yours is the same

Good luck

---

### Post by Harry33 on 2011-03-05
> **plucky said:**
> I had this problem caused by libcanberra-gtk3-0 & libcanberra-gtk3-module not installing causing libcanberra-gtk0  not to upgrade.
Open Synaptic Package Manager and navigate to **Status > Not Installed** and see what is there.I had to mark libcanberra-gtk3-0 & libcanberra-gtk3-module to be upgraded first and after that was upgraded it would then upgrade libcanberra-gtk0.
The indicator in the panel then disappeared.
See if yours is the same
Good luck

Ubuntu Natty does not use any longer GTK+3 based libcanberra packages.
You ought to be able to remove without problems.
I have these libcanberra packages installed:
- gnome-session-canberra
- libcanberra-gtk-module
- libcanberra-gtk0
- libcanberra0

I use the version 0.26-1ubuntu10, because the newer 0.28-0ubuntu1 does not work regarding system-ready and login sounds.

There is, however, a new version building in Launchpad.
Here:
[https://launchpad.net/ubuntu/natty/+source/libcanberra/0.28-0ubuntu3](https://launchpad.net/ubuntu/natty/+source/libcanberra/0.28-0ubuntu3)

---

### Post by coffeecat on 2011-03-05
> **plucky said:**
> I had this problem caused by libcanberra-gtk3-0 & libcanberra-gtk3-module not installing causing libcanberra-gtk0  not to upgrade.

Open Synaptic Package Manager and navigate to **Status > Not Installed** and see what is there.I had to mark libcanberra-gtk3-0 & libcanberra-gtk3-module to be upgraded first and after that was upgraded it would then upgrade libcanberra-gtk0.

Yes, that's the solution - thanks. I'd been getting the same error in Synaptic since yesterday. 'sudo apt-get upgrade' and 'sudo aptitude safe-upgrade' would upgrade some stuff without any mention of libcanberra, but apt-get dist-upgrade revealed what the problem was:

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies.
 libcanberra-gtk0 : Breaks: libcanberra-gtk3-0 (< 0.28-0ubuntu1) but 0.26-1ubuntu9 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by Harry33 on 2011-03-05
I have tested the newest libcanberra (0.28-0ubuntu3):
[https://launchpad.net/ubuntu/natty/+source/libcanberra/0.28-0ubuntu3](https://launchpad.net/ubuntu/natty/+source/libcanberra/0.28-0ubuntu3)

It works fine. Also the system-ready and login sounds are OK now.

---

### Post by rburkartjo on 2011-03-05
tks ya'll got it fixed

---

### Post by bjesus on 2011-03-05
How did you all got it fixed?
My system is completely broken...

```
&#10140;  ~  sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 aisleriot : Depends: libcanberra-gtk0 (>= 0.17) but it is not installed
 cheese : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 empathy : Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
 gdm : Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
 gnome-control-center : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 gnome-games-common : Depends: libcanberra-gtk0 (>= 0.17) but it is not installed
 gnome-media : Depends: libcanberra-gtk0 (>= 0.13) but it is not installed
 gnome-panel : Depends: libcanberra-gtk0 (>= 0.17) but it is not installed
 gnome-power-manager : Depends: libcanberra-gtk0 (>= 0.17) but it is not installed
 gnome-screenshot : Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
 gnome-session-canberra : Depends: libcanberra-gtk0 but it is not installed
 gok : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 libbrasero-media1 : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 libcanberra-gtk-module : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 libcheese-gtk18 : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 libevolution : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 metacity : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
 nautilus-sendto-empathy : Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
 quadrapassel : Depends: libcanberra-gtk0 (>= 0.17) but it is not installed
 transmission-gtk : Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
E: Unmet dependencies. Try using -f.
```apt-get install -f and apt-get dist-upgrade -f gives me the same error...

UPDATE: well nevermind, I went on with some aptitude solution and later on I could reinstall everything I had removed... all fine now

---


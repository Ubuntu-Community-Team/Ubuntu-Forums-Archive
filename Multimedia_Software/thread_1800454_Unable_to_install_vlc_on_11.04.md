---
title: "Unable to install vlc on 11.04"
date: 2011-07-09
forum: Multimedia Software
---

### Post by f145h on 2011-07-09
This is what happens when i try to install vlc from terminal

f145h@f145h-System-Product-Name:~$ sudo apt-get install vlc
[sudo] password for f145h: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: libcucul0 (>= 0.99.beta13b-1) but it is not going to be installed
       Depends: vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Broken packages

I accidentally disconnected the net while installing the same from ubuntu software centre.
I'm using Ubuntu 11.04
Please help

---

### Post by linuxman94 on 2011-07-09
Try this command without any package name.

```
sudo apt-get install -f
```

---

### Post by garvinrick4 on 2011-07-09
##If previous post does not do it.
#Go to Software Sources and make sure you have your repositories open as per below:
Open a nautilus window, go to file system to /etc to /apt to sources.list and
right click and open with Software Sources and make sure all box's checked.
Main,Universe,restricted,multiverse.
Open a terminal: Ctrl/alt/t   :now copy and paste these below one at a time:
```
 
sudo apt-get update
sudo apt-get purge vlc
sudo apt-get update && sudo apt-get upgrade
sudo apt-get ubuntu-restricted-extras
sudo apt-get install vlc
sudo dpkg --configure -a
 

```First one updates repositories
next gets rid of all parts vlc 
next updates and upgrades system
next installs restricted extras such as codec's, java, flash, gstreamer if some already installed will not bother.
next installs vlc with no dependency problems.
last checks that know broken packages.

---


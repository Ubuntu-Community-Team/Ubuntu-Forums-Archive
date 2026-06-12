---
title: "ubuntu 9.10 vlc installation problem"
date: 2010-03-05
forum: Multimedia Software
---

### Post by golden_eye_ on 2010-03-05
hello all ... 
i am trying to install vlc in 9.10 thorugh "sudo apt-get install vlc" command
but its generating the following error message ...

> 
sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.2-1ubuntu2.1) but it is not going to be installed
       Depends: libqtcore4 (>= 4.5.1) but it is not installable
       Depends: libqtgui4 (>= 4.5.1) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libtar but it is not installable
       Depends: libx264-67 (>= 1:0.svn20090502) but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
       Recommends: vlc-plugin-pulse (= 1.0.2-1ubuntu2.1) but it is not going to be installed
E: Broken packages

problem is same if i use synaptic package manager
what is the solution ??

another Q:
what is the problem for installing vim ??
> 
sudo apt-get install vim
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vim has no installation candidate


Thanks in advance

---

### Post by MelDJ on 2010-03-06
have you activated the multiverse repo in software sources?

---

### Post by golden_eye_ on 2010-03-06
ya

---

### Post by th0mas on 2010-05-09
same prob as here :

[http://ubuntuforums.org/showthread.php?t=1477568](http://ubuntuforums.org/showthread.php?t=1477568)

---


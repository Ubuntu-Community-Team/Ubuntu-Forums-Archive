---
title: "k9Copy suddenly stopped."
date: 2009-03-09
forum: Multimedia Software
---

### Post by timZZ on 2009-03-09
Hi,

I was a happy k9copy user but after shortly installing it less then a month ago it has disappeared out of my applications > sound & video.

I tried reinstalling and I get this from the terminal

#Blanked#@#Blanked#:~$ sudo apt-get install k9copy
[sudo] password for #Blanked#: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  k9copy: Depends: kdebase-runtime (>= 4:4.0.66) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.0.98a) but it is not going to be installed
          Depends: libphonon4 (> 4:4.2~) but it is not going to be installed
          Depends: libqt4-dbus (>= 4.4.0) but it is not installable
          Depends: libqt4-opengl (>= 4.4.0) but it is not installable
          Depends: libqt4-qt3support (>= 4.4.0) but it is not going to be installed
          Depends: libqt4-xml (>= 4.4.0) but it is not installable
          Depends: libqtcore4 (>= 4.4.0) but it is not installable
          Depends: libqtgui4 (>= 4.4.0) but it is not installable
          Depends: phonon (> 4:4.2~) but it is not installable
          Depends: mencoder but it is not going to be installed
E: Broken packages

---


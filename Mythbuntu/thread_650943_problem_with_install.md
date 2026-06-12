---
title: "problem with install"
date: 2007-12-27
forum: Mythbuntu
---

### Post by docdailey on 2007-12-27
I am having a heck of a time here on a new system...

it is a converted thin client (now thick client) that I am installing mythbuntu on to use as a front end...I suspect something in my ubuntu install is broke (I have never had any problems like this...

Here is what I get:

willy@mini:~$ sudo apt-get install mythbuntu-desktop
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythbuntu-desktop: Depends: gsfonts-x11 but it is not installable
                     Depends: mythbuntu-control-centre but it is not going to be installed
                     Depends: mythbuntu-default-settings but it is not going to be installed
                     Depends: mythtv-common but it is not going to be installed
                     Depends: thunar but it is not installable
                     Depends: xfce4-mcs-manager but it is not installable
                     Depends: xfce4-mcs-plugins but it is not installable
                     Depends: xfce4-mixer but it is not installable
                     Depends: xfce4-panel but it is not installable
                     Depends: xfce4-session but it is not installable
                     Depends: xfce4-terminal but it is not installable
                     Depends: xfce4-utils but it is not installable
                     Depends: xfdesktop4 but it is not installable
                     Depends: xfwm4 but it is not installable
                     Recommends: xfce4-icon-theme but it is not installable
                     Recommends: xfwm4-themes but it is not installable
E: Broken packages


Any help fixing this?

Bill

---

### Post by superm1 on 2007-12-27
Sounds like you don't have universe and/or multiverse on.

---

### Post by docdailey on 2007-12-27
Well. I got it fixed.  I figured it was something to do with my sources.list.  I was also having problems installing automatix2 so they recommeneded a sources.list (faq) and I replaced mine with theirs.  Turns out some of my debs were not verified properly during install for some reason.  I thought I had checked them but apparently not.

Thanks,

Bill

---

### Post by superm1 on 2007-12-27
> **docdailey said:**
> Well. I got it fixed.  I figured it was something to do with my sources.list.  I was also having problems installing automatix2 so they recommeneded a sources.list (faq) and I replaced mine with theirs.  Turns out some of my debs were not verified properly during install for some reason.  I thought I had checked them but apparently not.

Thanks,

Bill
For future reference: stay away from automatix, okay?  For most purposes, you can simply enable universe and multiverse in software sources and get away fine.

---

### Post by docdailey on 2007-12-31
Will do on the Automatix.  I have never heard that.  I am sure it was my sources.list.  The install disabled some and it was a jumbled mess...cleaned up now.

Bill

---


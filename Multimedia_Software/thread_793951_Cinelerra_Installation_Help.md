---
title: "Cinelerra Installation Help"
date: 2008-05-14
forum: Multimedia Software
---

### Post by Edrahil on 2008-05-14
I've been having trouble installing the video editing program Cinelerra on my 8.04 laptop. This is the output I get from running apt-get

I also tried finding the  libquicktimehv-generic package and only found one for the HPPA architecture



edrahil@edrahil-laptop:~$ sudo apt-get install cinelerra-generic
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
  cinelerra-generic: Depends: libquicktimehv-generic (= 1:2.1.0-1svn20080503akirad1) but it is not going to be installed
E: Broken packages


Thank you!

---


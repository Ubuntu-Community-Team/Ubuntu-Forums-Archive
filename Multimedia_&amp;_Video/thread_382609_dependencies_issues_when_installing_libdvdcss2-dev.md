---
title: "dependencies issues when installing libdvdcss2-dev"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by fearevilleet on 2007-03-12
Hello.

I have been trying to install google	Picasa but  libdvdcss2-dev is not installed. I have not been able to install it do to a dependencies issues. Below is the code I put in. I also tried to install it with automatirx2, but it failed because it was missing  libdvdcss2-dev. If some one could tell me what I am doing wrong when trying to install libdvdcss2-dev it would be appreciated. 

```
evilleet@box:~$ sudo apt-get install picasa
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.5-1) but 1.2.9-2medibuntu2 is to be installed
  xvattr: Depends: xlibs (> 4.1.0) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
evilleet@box:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdcss2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdvdcss2-dev: Depends: libdvdcss2 (= 1.2.5-1) but 1.2.9-2medibuntu2 is to be installed
  xvattr: Depends: xlibs (> 4.1.0) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
evilleet@box:~$ sudo apt-get install libdvdcss2 xvattr xlibs
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdcss2 is already the newest version.
xvattr is already the newest version.
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xkb-data libxft1
E: Package xlibs has no installation candidate
evilleet@box:~$

```

---

### Post by El_Matthews on 2007-03-12
start by 'apt-get -f install' and then you can download all files needed for libdvdcss from [http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)

---


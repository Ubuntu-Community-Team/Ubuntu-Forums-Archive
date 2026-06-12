---
title: "mysql-query-browser cannot fulfill dependencies"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by locovaca on 2011-04-10
Attempting to install mysql-query-browser on a fresh install of Kubuntu Beta 1 fails due to dependencies

```
dan@Aerostar:~$ sudo aptitude install mysql-query-browser
The following NEW packages will be installed:
  gamin{a} gnome-mime-data{a} libatkmm-1.6-1{a} libbonobo2-0{a} libbonobo2-common{a} libcairomm-1.0-1{a} libgamin0{a} libglade2-0{a} libglibmm-2.4-1c2a{a} libgnome2-0{a} libgnome2-common{a} libgnomevfs2-0{a} libgnomevfs2-common{a} 
  libgtkmm-2.4-1c2a{a} libpangomm-1.4-1{a} mysql-query-browser{b} 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,643 kB of archives. After unpacking 20.5 MB will be used.
The following packages have unmet dependencies:
  mysql-query-browser: Depends: mysql-gui-tools-common (= 5.0r14+openSUSE-2.1) but it is not going to be installed.
                       Depends: libgtkhtml3.14-19 (< 1:3.31) but 1:3.32.2-0ubuntu1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     mysql-query-browser [Not Installed]                



Accept this solution? [Y/n/q/?] n

*** No more solutions available ***

The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     mysql-query-browser [Not Installed]                



Accept this solution? [Y/n/q/?] 

```

I have all repos enabled.  Any thoughts?

---

### Post by r-senior on 2011-04-10
It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/mysql-gui-tools/+bug/683817](https://bugs.launchpad.net/ubuntu/+source/mysql-gui-tools/+bug/683817)

There's a workaround in the comments if you are desperate for it.

---


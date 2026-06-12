---
title: "mythtv-status has unmet dependencies"
date: 2010-01-10
forum: Mythbuntu
---

### Post by dannyboy79 on 2010-01-10
here's what it says when I try to install mythtv-status from the .22 repos from the weekly builds repo.

The following packages have unmet dependencies:
  mythtv-status: Depends: libmyth-perl but it is not going to be installed
E: Broken packages

if i install libmyth-perl, then it says this:
The following packages have unmet dependencies:
  libmyth-perl: Depends: libmythtv-perl but it is not going to be installed
E: Broken packages

if i then try to intsall libmythtv-perl, i get this:
Reading state information... Done
libmythtv-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


yet mythtv-status wont install. ne help please?

---

### Post by thomi_ch on 2010-01-28
hi

same problem here...
in the irc channel i get a tip to install mythbuntu-control-center and install mythtv-status from there... but i don't found this option..

so.. what's the solution?

greetings
thomi

---

### Post by superm1 on 2010-01-28
Enable the testing repo (it's in mcc's repos plugin if you didn't enable it during repos install).

---


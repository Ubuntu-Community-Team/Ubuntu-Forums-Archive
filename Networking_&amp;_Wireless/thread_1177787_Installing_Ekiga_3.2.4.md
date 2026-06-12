---
title: "Installing Ekiga 3.2.4"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by geno123 on 2009-06-03
I am trying to install Ekiga 3.2.4 on Ubuntu 9.04 from the source files available on the Ekiga website.  All goes well with the installation of the required ptlib and opal pieces.  However, when I run configure in trying to install Ekiga itself, I get the following error message:

Package requirements (gtk+-2.0 >= 2.12.0) were not met:
No package 'gtk+-2.0' found

There are approximately one zillion gtk pieces in the Ubuntu repositories.  It is not at all clear to me which file or files need to be installed  I have already tried several with no luck.

Has anyone solved this problem?

---

### Post by xapient on 2009-06-21
it's  libgtk2.0-dev


you will encounter several other dependency problems..  just look for lib + name + dev and install everything you find...


gl

---


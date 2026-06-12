---
title: "libpython2.5.so.1.0cannot open share cannot open shared object file: No such file or"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Nuvious on 2010-07-27
When running the beta of blender 2.5, I get the following error.

blender: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory

In previous versions of ubuntu you could 'apt-get install python2.5' to resolve the issue, but it doesn't appear in any/all of the repositories.  Any help on where I can get python2.5 for lucid-lynx?

Thanks in advance for your time!

---

### Post by Nuvious on 2010-07-27
P.S. I found this solution, but I can't seem to install the ppa :/

[https://launchpad.net/~fkrull/+archive/deadsnakes](https://launchpad.net/~fkrull/+archive/deadsnakes)

Get the following error:

$~/Documents/Graphics/blender_models$ sudo add-apt-repository ppa:fkrull/deadsnakes

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FF3997E83CD969B409FB24BC5BB92C09DB82666C

gpg: requesting key DB82666C from hkp server keyserver.ubuntu.com

gpgkeys: HTTP fetch error 7: couldn't connect to host

gpg: no valid OpenPGP data found.

gpg: Total number processed: 0

---


---
title: "alsa-oss"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by I Tvivl on 2007-11-20
I've tried to install alsa, and it went quit well. but when I tried installing the libraries an oss-mixer (which I got from the same downloadguide on alsa-project.org) it keeps telling me I'm missing command called:

**install-exec-am** and
**install-data-am**

I tried installing as root with:

./configure
make install

on 7.10

I'm new to Linux, so please help me and please make it simpel.

Thanks
 R

---

### Post by colo on 2007-11-20
Don't install from source unless your distribution does not provide packages for the software you need: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=gutsy&release=all)

Synaptic/Adept/aptitude/apt-get will happily set all of those apps up for you.

---


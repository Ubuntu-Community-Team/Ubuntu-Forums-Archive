---
title: "apt-get update fails- no repositorie problem"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by pdcc on 2012-07-06
Hi,

I have a server with ubuntu server 11.10 and my apt-get update don't work.
I get this error:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  404  Not Found


my sources.list is that:


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted universe$
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# GIS no Ubuntu
deb [http://ppa.launchpad.net/ubuntugis/ppa/ubuntu](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/ubuntugis/ppa/ubuntu](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu) natty main
# P.Mapper
deb [http://www.pmapper.net/dl/debian](http://www.pmapper.net/dl/debian) binary/
deb [http://ppa.launchpad.net/georepublic/pgrouting/ubuntu](http://ppa.launchpad.net/georepublic/pgrouting/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/georepublic/pgrouting/ubuntu](http://ppa.launchpad.net/georepublic/pgrouting/ubuntu) oneiric main
deb [http://apt.opengeo.org/ubuntu](http://apt.opengeo.org/ubuntu) lucid main


After i make apt-get clean the apt-get update doens't work and i can't install nothing...

I now that repositories work because i downloaded some deb files with wget..

Anybody can help me please?

thanks

---

### Post by Elfy on 2012-07-06
Thread closed. Please do not post duplicates, it dilutes community effort.

---


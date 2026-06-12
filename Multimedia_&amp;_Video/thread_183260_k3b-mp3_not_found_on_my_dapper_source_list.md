---
title: "k3b-mp3 not found on my dapper source list"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by k420 on 2006-05-27
i cannot burn mp3s ahhhh!  It is not found by apt-get her is a copy of my source list. It sucks by the way please help! [CODE][# Automatically generated sources.list
 # http://www.ubuntulinux.nl/source-o-matic
 #
 # If you get errors about missing keys, lookup the key in this file
 # and run these commands (replace KEY with the key number)
 #
 # gpg --keyserver subkeys.pgp.net --recv KEY
 # gpg --export --armor KEY | sudo apt-key add -
 
 # Ubuntu supported packages (packages, GPG key: 437D05B5)
 deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
 deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
 deb http://security.ubuntu.com/ubuntu dapper-security main restricted
 
 # Ubuntu community supported packages (packages, GPG key: 437D05B5)
 deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
 deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
 deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
 
 # Backports & proposed
 deb http://mir1.ovh.net/ubuntu/ dapper-backports main universe multiverse restricted
 deb http://mir1.ovh.net/ubuntu/ dapper-proposed main universe multiverse restricted
 
 # Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
 
 # kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D508
 deb http://kubuntu.org/packages/kde-latest dapper main
 
 # Penguin Liberation Front (packages)
 #deb ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/ breezy free non-free
 
 # Bleeding edge wine packages (packages)
 deb http://wine.sourceforge.net/apt/ binary/
 
 # The Opera browser (packages)
 deb http://deb.opera.com/opera etch non-free
   
 # Multimedia
 deb ftp://ftp.nerim.net/debian-marillat sid main
 deb http://apt.cerkinfo.be/ unstable main contrib
 
 # checkgmail & xmms-wma
 deb http://gauvain.tuxfamily.org/repos dapper contrib
 
deb http://archive.ubuntu.com/ubuntu breezy main restricted

/CODE]

---

### Post by asimon on 2006-05-27
I think the package you search is called libk3b2-mp3. It's in universe. It was probably renamed somewhen.

---


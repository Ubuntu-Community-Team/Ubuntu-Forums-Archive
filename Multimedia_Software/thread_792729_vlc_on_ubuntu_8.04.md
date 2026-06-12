---
title: "vlc on ubuntu 8.04"
date: 2008-05-13
forum: Multimedia Software
---

### Post by _zax_ on 2008-05-13
after upgrading to ubuntu 8.04,vlc does not exist.

giving: 'sudo apt-get install vlc'

receiving:
 
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libvlc0
E: Package vlc has no installation candidate

---

### Post by Lucky LIX on 2008-05-13
A quick view in Synaptic packet manager tells me it should be in multiverse, named vlc .

---

### Post by _zax_ on 2008-05-13
i found vlc in synaptic package manager but after 'marking for installation' i get:

vlc:

Package vlc has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by cor2y on 2008-05-13
vlc is there.
Sounds like you didn't clean or remove your old source list when you upgraded to hardy.
If all the hardy repos are enabled (universe, restricted etc) it should be there.

---

### Post by _zax_ on 2008-05-13
i've made it : 

first step is to:
sudo pico /etc/apt/sources.list

and change line:
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy main restricted

to

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse

after that:
sudo aptitude update

and then:
sudo aptitude remove --purge vlc

and the final step [LoL]:
sudo aptitude install vlc

---


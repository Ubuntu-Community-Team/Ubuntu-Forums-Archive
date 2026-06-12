---
title: "Flash player install - libcurl3 dependency"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Tim Allen on 2009-04-30
Tried to install Flashplayer 10 so that I could use the BBC iplayer. Chose the Ubuntu option. Donload OK but installer gave the following error message: Dependency is notsatisfiable: libcurl3.

I'm a newbie to Linux so haven't a clue whatto do now!

---

### Post by Lintrix on 2009-07-15
first do this in terminal:
sudo apt-get install libcurl3

then you may install

---

### Post by TheParadox2 on 2009-07-15
I just installed ubuntu, and likewise Im new (but not brand new)...

I got an error in terminal after i used apt-get:

root@theparadox-desktop:/home/theparadox/Desktop# apt-get install libcurl3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libcurl3 has no installation candidate

...so... I'm not sure what to do next...

---

### Post by martinbaselier on 2009-07-15
It's in the repositories. Go to your configuration menu, choose software sources, and make sure universe and multiverse are checked.

---


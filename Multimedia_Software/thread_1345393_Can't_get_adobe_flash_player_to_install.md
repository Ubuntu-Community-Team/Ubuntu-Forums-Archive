---
title: "Can't get adobe flash player to install"
date: 2009-12-04
forum: Multimedia Software
---

### Post by skuzzel on 2009-12-04
I have ubuntu 9.04 and I just can't seem to get it to install. I down loaded the deb file from adobe and it says err: wrong architecture 1386. So I tried to install it through the terminal and it says it can't find the install. Leading me to believe that the repositories haven't been added, but I have just about every box checked in soft ware sources. That's the way 9.04 came for me. 

Any tips? If there is a problem with my repositories I'd like to get that updated as soon as possible. Also be aware, I'm still a bit slow with ubuntu.

---

### Post by lidex on 2009-12-04
Not a repository issue when install error states 'wrong architecture" on a downloaded deb. Are you using amd_64 install?
Anyway try this. Enter one command at a time into a terminal (accessories>terminal):
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer
```
if that doesn't work go here:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by skuzzel on 2009-12-04
Heh, I found the problem. I'm using a ps3, which is a PPC which doesn't work with flash, going to try gnash.

---


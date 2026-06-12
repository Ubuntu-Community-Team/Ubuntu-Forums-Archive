---
title: "Watching DVD's?"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2006-11-29
I just did a fresh install of 6.10 on my Dell X1 laptop and I am getting ready to travel and would love to watch some DVD's. Can someone please tell me how I can watch a DVD on my new Ubuntu system?

It appears that with the fresh install, Totem (Movie Player) is installed by default.

---

### Post by pay on 2006-11-29
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability)

---

### Post by CarlosinFL on 2006-11-29
I am trying to follow the guide however when I run the commands they suggest, it seems I don't have the proper repo's for them.

```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

```

This is what I get...

```
root@lptp:~# apt-get install libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread3

```

---

### Post by pay on 2006-11-30
Under the menu How to install DVD playback capability it says "Read #How to add extra repositories". click there and it will show the repositories needed.

---


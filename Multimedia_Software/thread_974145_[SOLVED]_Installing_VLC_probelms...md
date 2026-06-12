---
title: "[SOLVED] Installing VLC probelms.."
date: 2008-11-07
forum: Multimedia Software
---

### Post by cardpogi on 2008-11-07
Ok, I'm completely new to linux.. Setting up going great till now, except for the problem with my battery status display which is not the reason for this post though, I've been trying to get VLC to work when I got through the terminal
```
cardpogi@ubuntu:~$ apt-get install vlc\
> apt-get install vlc
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

``` And when I go Applications->Add/Remove Program
It plain fails.. :/  any ideas... not sure if I can actually login as root O and yeah I'm using Ubuntu 8.1

---

### Post by SuperSonic4 on 2008-11-07
```
sudo apt-get install vlc
```

That will grant temporary root privileges for the purpose of installing VLC

---

### Post by cardpogi on 2008-11-07
AAA... >< *Feels all stupid.. XD.. Thanks alot... I have alot to read and learn.. alot...

---


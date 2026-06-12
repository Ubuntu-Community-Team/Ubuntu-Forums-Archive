---
title: "VLC Goldeneye"
date: 2010-04-14
forum: Multimedia Software
---

### Post by vwbug on 2010-04-14
Anyone know how to get VLC Goldeneye 1.02. or higher, for Hardy?  I really like it but haven't found it available for Hardy.  I know its available for Ubuntu 9.10, but I don't really care for that release:(

There are some .flv files that will only play on Goldeneye, and its just a better player than the older ones.

I have a dual boot for 8.04 and 9.10, but its a pain to reboot just to use a different player.

---

### Post by WinterRain on 2010-04-14
Do:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D
```
Then add these 2 lines to your sources list.
```
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main

deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main
```
Then:
```
sudo apt-get update
```
Then check synaptic to see what version is available. But according to launchpad, the highest version available for hardy is .99

You could also compile it yourself. Good luck.

---

### Post by vwbug on 2010-04-14
Thanks winterrain, but been there done that. The info is correct, it will only update to 0.9. Hope Ubuntu 10.04 is better than 9.10.

---


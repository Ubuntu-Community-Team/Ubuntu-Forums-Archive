---
title: "Handbrake"
date: 2011-06-07
forum: Multimedia Software
---

### Post by blackbird34 on 2011-06-07
Hi 

I've been trying to install Handbrake (video converter) but its not in main repositories. So i went [here]("http://www.hackourlife.com/install-handbrake-on-ubuntu-10-04/") and [here]("http://www.jonathanmoeller.com/screed/?p=2991") to try and find a way to add the PPA. I got more or less the same error both times:

```
https://launchpad.net/api/1.0/~stebbins/+archive/handbrake-snapshots: <urlopen error [Errno 8] _ssl.c:499: EOF occurred in violation of protocol>
```and this:
```
https://launchpad.net/api/1.0/~stebbins/+archive/handbrake-releases: <urlopen error [Errno 8] _ssl.c:499: EOF occurred in violation of protocol>

```What can i do?

---

### Post by blackbird34 on 2011-06-07
In the end i worked it out with [this]("http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty"):
```
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

then
```
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu natty-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
```

then sudo apt-get install handbrake-gtk. Hope nobody else has any trouble.

---

### Post by Bucky Ball on 2011-06-07
You've probably prevented some from having the same problem. Thanks for sharing ... ;)

---


---
title: "After apt-get upgrade mplayer doesn't work - can't find libjpeg"
date: 2013-03-20
forum: Multimedia Software
---

### Post by rabbitambulance on 2013-03-20
I ran apt-get upgrade, and now mplayer just throws this error:

```
mplayer: error while loading shared libraries: libjpeg.so.62: cannot open shared object file: No such file or directory

```

If I try to install mplayer, this happens:
```
sudo apt-get install mplayerReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
  libglib2.0-0: Breaks: gvfs (< 1.8) but 1.6.1-0ubuntu1build1 is to be installed
  libpango1.0-0: Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu2.2 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8-0ubuntu3.3 is to be installed
       Breaks: network-manager-pptp (<= 0.8.0.999-1) but 0.8-0ubuntu3 is to be installed
E: Broken packages

```

Any hints?

---

### Post by andrew.46 on 2013-03-23
Upgrading can cause a few problems, I have to admit that I prefer a clean install. Can you post the contents of */etc/apt/sources.list*? (and the contents of any files in */etc/apt/sources.list.d/*) You may have conflicting repositories in there...

---

### Post by SeijiSensei on 2013-03-23
Did you run "sudo apt-get update" before apt-get upgrade?

---


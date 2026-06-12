---
title: "Devede not installing..NEED HELP PLEASE :)"
date: 2009-11-21
forum: Multimedia Software
---

### Post by gordong11 on 2009-11-21
I ran my update manager and it uninstalled DeveDe for some reason. The update manager ran an update for mplayer and mencoder which caused this problem. I think. Now when I goto re-install devede I get dependency problems.

Depenency errors that Synaptic package Manager wont install:

libavformat-extra-52
libpostproc-extra-51
libswscale-extra-0

Ok. So I try to manually install extra packages above and it removes the non-extra counterpart, but even tho i have 3 files installed, i am still getting the same error.

Are there repositories for Devede, mplayer, mencoder that i need to activate? all are activated in Sources menu.

added: I installed Mplayer, and the tried install DeveDe, package manager wanted to remove Mplayer, and got the same 3 dependency error.

IS there a DeVeDe alternative? I love DeVeDe, but I need something.

Devede depends on mencoder, and mencoder uninstalls the 3 packagaes above and replaces with non extra version. If i unstall mencoder and try to install devede, i get needs mencoder error and wont install.

It's a cycle I can't break.

---

### Post by HappyFeet on 2009-11-21
First, let's clean out your system of unwanted cruft:
```
sudo apt-get clean && sudo apt-get autoremove
```
You may have broken packages, so:
```
sudo dpkg --configure -a && sudo apt-get install -f
```

Lastly, try installing the medibuntu repos: 
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

Let us know how it goes.

---

### Post by gordong11 on 2009-11-24
Thanks so much, worked like a charm!!

---


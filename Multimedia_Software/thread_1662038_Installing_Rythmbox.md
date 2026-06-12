---
title: "Installing Rythmbox"
date: 2011-01-07
forum: Multimedia Software
---

### Post by nova47 on 2011-01-07
I'm not running gnome but I'm a big fan of Rythmbox (Sorry if your an Amarok fan but I just can't stand it lol). I've been attempting to get it up and running and have been installing the dependencies piece by piece (isn't that always fun). I've found most of them but I've gotten hung up on this:

Requested 'gtk+-2.0 >= 2.18.0' but version of GTK+ is 2.14.4
Requested 'libsoup-2.4 >= 2.26.0' but version of libsoup is 2.24.1
No package 'libsoup-gnome-2.4' found

I imagine I'm going to have to compile it myself but having never bothered using make files before and was wondering if anyone knew either 1) an easier place to just download libsoup-gnome to my system or 2) How one goes about downloading and compiling it manually via the makefiles. (I found libsoup-gnome here [http://live.gnome.org/LibSoup](http://live.gnome.org/LibSoup) but it looks a little daunting)

---

### Post by Zzl1xndd on 2011-01-07
I could be wrong (I haven't used Kubuntu in a long time) but you should be able to use the package manger to install Rythmbox with no dependency hell.

---

### Post by ajgreeny on 2011-01-07
As tweakedenigma says, you can install rhythmbox using the packager manager.  Just make sure your software sources are updated, and your system is also fully updated.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install rhythmbox
``` should do it for you with no difficulty.

---

### Post by nova47 on 2011-01-07
hahaha to be completely and openly honest I asked the question a bit out of turn I'm not actually running Ubuntu I'm running a variant of Slax.

---


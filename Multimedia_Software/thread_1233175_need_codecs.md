---
title: "need codecs"
date: 2009-08-06
forum: Multimedia Software
---

### Post by karumudi7 on 2009-08-06
Hi I need audio,video codecs for my newly installed UBUNTU 8.04 non-internet PC.
Is it possible to dwld from websites and install on a non-internet PC?
If so pls help me!
Thanks

---

### Post by harry2006 on 2009-08-06
yes , there are quite a lot of ways of doing this...one of them is usign aptonCD , just google for it.
have a look here,
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
[http://linuxappfinder.com/package/aptoncd](http://linuxappfinder.com/package/aptoncd)

---

### Post by ajgreeny on 2009-08-06
If the internet enabled PC does not run ubuntu it is no help using aptoncd as it is a linux application only as far as I'm aware.  However you can open synaptic on your ubuntu PC and select and mark the applications/codecs etc etc you want to install, then go to **File-Save markings as** and save a text file to /home.

Now on the windows PC if that is the only one available, go to [http://packages.ubuntu.com/jaunty/allpackages](http://packages.ubuntu.com/jaunty/allpackages) where you can download the packages listed on the text file, slow and tedious, perhaps but will get it done.  Now take those .deb packages and copy them as admin to /var/cache/apt/archives on the ubuntu PC, reload the list in synaptic and repeat the installation of apps/codecs etc etc.  As the .debs are now in cache, they will be installed as if you had internet access.

---


---
title: "amarok 2.3.2 with Gnome"
date: 2010-09-23
forum: Multimedia Software
---

### Post by aqshin on 2010-09-23
How can I install Amarok 2.3.2 (recent version) in Ubuntu? 

I downloaded the source file and looked at the README file. It says I need to have some dependencies before installing. But since Amarok is for KDE, it would be frustrating to get all the dependencies correctly in Gnome. Or is there another way to do it?

---

### Post by qamelian on 2010-09-23
If all the minimum dependencies are available in the standard Ubuntu repos (which is often the case), you can have apt install the dependencies for you by opening a terminal and executing:
```
sudo apt-get build-dep amarok
```Then just follow the instructions in the readme to compile and install amarok.

---

### Post by aqshin on 2010-09-25
thanks.. I did that, and after
```
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` 
```

it gave me error: "TagLib version too old: version searched :1.6, found 1.5"

I searched for the package on the internet and installed it manually, but still the same error. The package I installed is "taglib-1.6.3"

any clue what might be the problem?

---

### Post by Yellow Pasque on 2010-09-25
What version of ubuntu are you using?  You're probably better off trying to find a PPA/.deb rather than building from source.

---

### Post by aqshin on 2010-09-25
I am using Ubuntu 9.04 (i am afraid to upgrade it becuse of some hardware problem).

The problem is that Amarok is for KDE, but the desktop environment I am using is GNOME. The older versions of Amarok could be installed from Synaptic or apt-get, and that would automatically install many KDE packages. At the moment, by this method only older version is available.

---

### Post by aqshin on 2010-10-06
Finally it worked! After installing ubuntu 10.04,

[http://www.techdrivein.com/2010/06/install-stunning-new-amarok-231-bell-in.html](http://www.techdrivein.com/2010/06/install-stunning-new-amarok-231-bell-in.html)

still some little bugs with amarok, but it gets better..

---


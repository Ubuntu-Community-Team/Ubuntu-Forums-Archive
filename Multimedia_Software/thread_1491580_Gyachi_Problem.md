---
title: "Gyachi Problem"
date: 2010-05-23
forum: Multimedia Software
---

### Post by Gold_Eyes on 2010-05-23
Hi everybody .
Yestarday i tryed to Compile gyachi-1.1.71  on ubuntu 10.04 LTS (32 Bit) form sources and i realy don't know what is wrong in there.
Here is what i done:
Downloaded the gyachi (source) , extracted, Readed the INSTALL.txt  and when i tryed to compile it i got the following message:
> checking for gpgme.h... no
configure: error: cannot find include file gpgme.h. Perhaps you need to install the gpgme development package?[this ***normally*** means that i don't have  probably installed libgpgme11 or libgpgme11-dev so i typed the follow]("http://www.google.com/search?hl=en&ei=I8P5S9ibEYSJOP-i0JUM&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CBEQBSgA&q=this+normally+means+that+i+don%27t+have+probably+installed+libgpgme11+or+libgpgme11-dev+so+i+typed+the+follow&spell=1")ing :
```
sudo apt-get install libgpgme11 libgpgme11-dev
```and here is my output which says that i have it already installed:
> sudo apt-get install libgpgme11 libgpgme11-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgpgme11 is already the newest version.
libgpgme11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.now i am realy stuck in here , please need help about what should i do . Thank you .

---

### Post by byStanderone on 2010-05-23
...just for info, gyachi for karmic also works well in lucid, i mean the pre-compiled version.

---

### Post by Gold_Eyes on 2010-05-24
> **byStanderone said:**
> ...just for info, gyachi for karmic also works well in lucid, i mean the pre-compiled version.
where can i find pre-compiled version? and is there any chance to fix my above problem ?

---

### Post by byStanderone on 2010-05-25
...not sure about your compiling procedure, tho ver. 1.2.6 is available at sourceforge :
 [http://sourceforge.net/projects/gyachi/files/gyachi/1.2.6/gyachi-1.2.6.tar.gz/download](http://sourceforge.net/projects/gyachi/files/gyachi/1.2.6/gyachi-1.2.6.tar.gz/download)

 haven't tried this yet for am still using ver. 1.2.2 both in karmic ang lucid.

---

### Post by proggy on 2010-05-25
[https://launchpad.net/~loell/+archive/ppa/+build/1140332](https://launchpad.net/~loell/+archive/ppa/+build/1140332) You can also try here or here [https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)

---

### Post by byStanderone on 2010-05-25
...if you want it to be from sourceforge, browse a bit downward on this page and look for ver 1.2.2 tar.gz :

[http://sourceforge.net/projects/gyachi/files/](http://sourceforge.net/projects/gyachi/files/)

---

### Post by Linuxforall on 2010-05-25
[https://launchpad.net/~baudm/+archive/ppa](https://launchpad.net/~baudm/+archive/ppa)  Latest gyachi can be found here, it works quite well on my x64 Lucid.

---


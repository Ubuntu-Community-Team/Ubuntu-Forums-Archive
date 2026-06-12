---
title: "can't install .deb packages"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by hourna on 2010-09-01
it seems that i can't install .deb packages. i have downloaded the .deb of both opera 10.70 and play on linux packages and none of them have been installed. package manager says installation was complete but it is not. my ubuntu 10.10 beta is 64 bit and also the packages were.

---

### Post by wojox on 2010-09-01
Did you try to install with Gdebi? Also

```
sudo dpkg -i --force-architecture NameOfPackage.deb
```

---

### Post by hourna on 2010-09-01
(Reading database ... 149032 files and directories currently installed.)
Preparing to replace opera 10.70.9036 (using opera_10.70.9036_amd64.deb) ...
Unpacking replacement opera ...
Setting up opera (10.70.9036) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for python-support ...

that is all.

---

### Post by cariboo on 2010-09-01
What happens when you type:

```
opera
```

in a terminal?

---

### Post by kyleabaker on 2010-09-01
> **hourna said:**
> it seems that i can't install .deb packages. i have downloaded the .deb of both opera 10.70 and play on linux packages and none of them have been installed. package manager says installation was complete but it is not. my ubuntu 10.10 beta is 64 bit and also the packages were.

You should always search before you start new threads. ;)

[http://my.opera.com/desktopteam/blog/new-10-70-snapshot-synchronizing-build-numbers-almost#comment37897572](http://my.opera.com/desktopteam/blog/new-10-70-snapshot-synchronizing-build-numbers-almost#comment37897572)
[http://ubuntuforums.org/showthread.php?t=1273828](http://ubuntuforums.org/showthread.php?t=1273828)
[http://ubuntuforums.org/showthread.php?t=1276674](http://ubuntuforums.org/showthread.php?t=1276674)

---

### Post by hourna on 2010-09-01
opera opens but it is the older opera. 10.61.

---

### Post by kyleabaker on 2010-09-01
> **hourna said:**
> opera opens but it is the older opera. 10.61.

This seems to always happen around these stages of Ubuntu development. Read through the last link I posted above.

---

### Post by mc4man on 2010-09-01
the 32 bit .deb  seems fine - does terminal confirm old version? (possibly you have new anyway...
> doug@doug-laptop:~$ opera --version
Opera 10.70. Build 9013 for Linux.
Compiled on Aug 17 2010 by gcc 4.3.2 (ABI: 1002) for GNU libc 2.7.


---

### Post by ronacc on 2010-09-01
the 64bit .deb of Opera 10.61 won't install but you can d/l the tar.gz or tar.bz2 and then unzip it into a directory in you /home and run it from there with ./opera in a term in that dir .

---

### Post by jppr on 2010-09-02
I installed yesterday Opera 10.70 [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)
gdebi works fine and Opera works fine too ;)

---


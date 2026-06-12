---
title: "lmms package error"
date: 2007-12-19
forum: Multimedia Production
---

### Post by linuxmann on 2007-12-19
I have the error message "error: dependency is not satisfiable: libasound2" when i attempt to install the main (not common) .deb i386 package. I have ubuntu 7.04. what should i do?


I downloaded the packages from the [http://lmms.sourceforge.net/download.php](http://lmms.sourceforge.net/download.php) page under ubuntu

---

### Post by Stochastic on 2007-12-19
try running ```
sudo apt-get install libasound2
``` and if that doesn't solve the problem then try ```
sudo apt-get install libasound2-dev
```

---


---
title: "Installing dvr-3.2"
date: 2009-04-15
forum: Multimedia Software
---

### Post by LinuxMaege on 2009-04-15
Hello all, I am trying to install a program called dvr-3.2, which is supposedly a audio and video recording program. I have done some research as to what I need to do to get it to install, but all attempts have failed so far. I am trying to install via Terminal and this is what I see

ezra@ezra-laptop:~/Desktop/dvr-3.2$ make
cd lib && make
make[1]: Entering directory `/home/ezra/Desktop/dvr-3.2/lib'
make[1]: `libdvr.a' is up to date.
make[1]: Leaving directory `/home/ezra/Desktop/dvr-3.2/lib'
cd dvr-console && make
make[1]: Entering directory `/home/ezra/Desktop/dvr-3.2/dvr-console'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ezra/Desktop/dvr-3.2/dvr-console'
cd dvr-qtgui && ./configure && make
./configure: 9: Syntax error: "(" unexpected
make: *** [all] Error 2

Any help would be appreciated. Thank you in advance!

---

### Post by LinuxMaege on 2009-04-15
I am installing this program onto a ubuntu 8.04 installation. Thanks again for you assistance.

---


---
title: "Problem installing KM to get ati capture working."
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by papafreebird on 2008-01-30
Hello I am trying to install km to get capture capabilities with my all in wonder card.  I am following this guide
[http://ubuntuforums.org/showthread.php?t=111672](http://ubuntuforums.org/showthread.php?t=111672)

When it try to install km I get this error message.  


steven@steven-desktop:~/Desktop/km$ sudo make
[sudo] password for steven:
make -C /lib/modules/2.6.22-14-generic/build M=/home/steven/Desktop/km modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/steven/Desktop/km/km_api.o
/home/steven/Desktop/km/km_api.c:22:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/steven/Desktop/km/km_api.o] Error 1
make[1]: *** [_module_/home/steven/Desktop/km] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2



Any clues what I'm doing wrong?

---


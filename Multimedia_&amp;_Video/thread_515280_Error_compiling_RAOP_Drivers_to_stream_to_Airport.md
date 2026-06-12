---
title: "Error compiling RAOP Drivers to stream to Airport"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by fictivetoast on 2007-08-01
Hey all - I'm trying to stream music to an airport from Feisty using raop as mentioned at [http://ubuntuforums.org/showthread.php?t=432713&highlight=raop](http://ubuntuforums.org/showthread.php?t=432713&highlight=raop) and elsewhere.

I've made and installed the main raop package, but when I try to make the raop drivers package, I choke immediately on this error:

brandon@brandon-laptop:~/SVN/raop_play-0.5.1/drivers$ make
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=/home/brandon/SVN/raop_play-0.5.1/drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/brandon/SVN/raop_play-0.5.1/drivers/alsa_raoppcm.o
/home/brandon/SVN/raop_play-0.5.1/drivers/alsa_raoppcm.c:23:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/brandon/SVN/raop_play-0.5.1/drivers/alsa_raoppcm.o] Error 1
make[1]: *** [_module_/home/brandon/SVN/raop_play-0.5.1/drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [2.6.] Error 2

What does "error: linux/config.h: No such file or directory" mean and how can I overcome it?

Thanks in advance!

---

### Post by fictivetoast on 2007-08-01
fixed

by doing:
 ln -s autoconf.h config.h
in /usr/src/linux-headers-2.6.20-16-generic/include/linux

---

### Post by __Alex__ on 2007-10-22
Somebody wrote a patch to make raop compliant with the new situation, works pretty well
check out :
[http://www.jroller.com/nwinkler/entry/raop_play_and_kernel_2](http://www.jroller.com/nwinkler/entry/raop_play_and_kernel_2)

Tried it and works perfect for me, compilation is just fine.

---


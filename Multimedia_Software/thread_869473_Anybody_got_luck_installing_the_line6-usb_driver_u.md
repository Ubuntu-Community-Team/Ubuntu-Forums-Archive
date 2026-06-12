---
title: "Anybody got luck installing the line6-usb driver under Hardy Heron?"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Bibiwinter on 2008-07-24
Hi all,

  I've been trying for a while to install the line6-usb driver for my PodXT on Hardy Heron, but I have had no luck so far.  I tried with the driver found here:  [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/) 

  Here is the output I got when trying:

root@Tweety:/home/seb/Desktop/Driver PodXT/line6usb-0.7.3# sudo make install
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/seb/Desktop/Driver PodXT/line6usb-0.7.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `PodXT/line6usb-0.7.3'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

My system is Hardy Heron with:

root@Tweety:/home/seb/Desktop/Driver PodXT# uname -a
Linux Tweety 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

Anybody got more luck than I?  I googled and looked around in several forums and couldn't find anything so far.

Thanks!

---


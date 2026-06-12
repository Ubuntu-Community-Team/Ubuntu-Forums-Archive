---
title: "King Bahamut, Ndiswrapper, and Linksys Wireless"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by damianubuntu on 2006-04-19
Hi all,
I tried to use Ndiswrapper as detailed here for a new Acer USB wireless, but no joy.  Decided to change the Acer for a Linksys WUSB54g v.4 since the forums and wiki's suggest it is fairly well supported.  Then used this article by King Bahumut

[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

to try to install the required driver.

What I get after 'sudo make install' is

echo "2.6 module install"
2.6 module install
make -C /lib/modules/2.6.12-9-686/build SUBDIRS=/home/damian/rt2570-1.1.0-b1/Module modules_install
make: *** /lib/modules/2.6.12-9-686/build: No such file or directory.  Stop.
make: *** [modules_install] Error 2


Any suggestions what's gone wrong, anyone?

Also I'm curious why so many posts here suggest people struggling with trying to get this device to work with Ndiswrapper, when it appears that its supported.  Is Ndiswrapper good to use anyway?

Thanks

---

### Post by KingBahamut on 2006-04-19
Ndiswrapper is good for use when only a last alternative. In my opinion.

---

### Post by damianubuntu on 2006-04-19
Hi, I hoped I'd get your attention by putting your name in the subject!!
What do you think I've done wrong?  I followed the instructions correctly (- I think!)

---


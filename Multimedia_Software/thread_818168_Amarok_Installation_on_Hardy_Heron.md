---
title: "Amarok Installation on Hardy Heron"
date: 2008-06-04
forum: Multimedia Software
---

### Post by rksingh54 on 2008-06-04
I have tried to install Amarok on my HP Pavilion dv 6225us that has a beautifully working UBUNTU 8.04 by both, Synaptic Package Manager and through Terminal. Install shows no problem but when trying to initialize to play I get a message:

"There was an error setting up inter-process communication for KDE. The message returned by the system was:

Could not read network connection list.
/home/rk/.dcopserver_dex2_0
Please check that the “dcopserver” program is running.

OK"

Upon clicking on OK, I get another message:

"Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net."


I am a newbie to Linux and even newer to UBUNTU; any help would be appreciated.

RKS

---

### Post by bjorn on 2008-06-04
Check this thread it might help:

[http://ubuntuforums.org/showthread.php?t=622563](http://ubuntuforums.org/showthread.php?t=622563)

---


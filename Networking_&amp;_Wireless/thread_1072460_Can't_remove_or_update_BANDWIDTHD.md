---
title: "Can't remove or update BANDWIDTHD"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by obscur156 on 2009-02-17
Hi all,i have installed a package "SARGE-bandwidthd_2.0.1_i386.deb" and i can't upgrade or remove it.Always getting an error message.

```
obi@LIBERTE:~$ sudo aptitude remove bandwidthd
[sudo] password for obi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  bandwidthd 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 201kB will be freed.
Writing extended state information... Done
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

```

I don't know what to do,i have tried everything i know with no success.
Help please,regards.

---

### Post by obscur156 on 2009-02-17
Ok solved it using a command from another thread but i just changed the package name with mine (bandwidthd) and it worked right away.
Thanks to plucky from this thread :
[http://ubuntuforums.org/showthread.php?t=1064526&highlight=Package+bad+inconsistent+state&page=2]("http://ubuntuforums.org/showthread.php?t=1064526&highlight=Package+bad+inconsistent+state&page=2")

Best regards and have a nice day.

---


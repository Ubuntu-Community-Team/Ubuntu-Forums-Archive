---
title: "ATI Catalyst 8.3 Driver Woes"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by Tristam Green on 2008-03-06
OK.  Using the steps put forth in [this thread](http://ubuntuforums.org/showthread.php?t=716543), I attempted to install the new ATI drivers for my machine.

While installing, I get this set of messages:

```
Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? n
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Errors were encountered while processing:
 fglrx-amdcccle_8.471-0ubuntu1_i386.deb
 fglrx-kernel-source
```

The install terminates, and when I restarted X, it now beige-screens after GDM login and reverts back to GDM.  I am able to select the Failsafe GNOME session in GDM but I cannot figure out what happened.

System Specs are in the signature, I previously was using the restricted drivers and was led to believe this would simply upgrade them.  Any chance I can "downgrade" them back to what they were?  And if so, how?


Thanks in advance for any help.


Tristam

---


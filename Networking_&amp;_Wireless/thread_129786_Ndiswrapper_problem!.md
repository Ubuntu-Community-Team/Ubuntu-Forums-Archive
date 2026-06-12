---
title: "Ndiswrapper problem!"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2006-02-14
I've screwed up my Ndiswrapper program in previous attempts at solving a Wifi hardware problem.  So I followed this uninstall tutorial the best I could: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall)
And it seems like removing the user space tools:
'ndiswrapper' (in /usr/sbin)  - OK
'loadndisdriver' (in /sbin)  - OK
[COLOR="Red"]kernel module 'ndiswrapper'  - ERROR[/COLOR]

Here's a snapshot at my attempts to uninstall ndiswrapper and unloading the module, followed by ignoring the ERROR and installing it anyways.
> **guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$** [COLOR="blue"]sudo make uninstall[/COLOR]
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper
[COLOR="Red"]/bin/rm: cannot remove `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1[/COLOR]
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**

> **guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$** [COLOR="Blue"]sudo modprobe -r ndiswrapper[/COLOR]
FATAL: Module ndiswrapper not found.
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**
> 
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$** [COLOR="Blue"]sudo make install[/COLOR]
make -C driver install
make[1]: Entering directory `/home/guest/Linux/ndiswrapper-1.9/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/guest/Linux/ndiswrapper-1.9/driver'
make: *** [install] Error 2
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**

What's wrong here?

---


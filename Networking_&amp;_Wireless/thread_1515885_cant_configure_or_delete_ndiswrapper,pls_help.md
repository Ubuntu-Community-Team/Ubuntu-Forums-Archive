---
title: "cant configure or delete ndiswrapper,pls help"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by yoyu007 on 2010-06-23
cant continue when i install or delete ndiswrapper


I got this message:


Errors were encountered while processing:
 ndiswrapper-dkms
Setting up ndiswrapper-dkms (1.56-1) ...
Removing old ndiswrapper-1.56 DKMS files...

------------------------------
Deleting module version: 1.56
completely from the DKMS tree.
------------------------------
Done.
Loading new ndiswrapper-1.56 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-5-generic
Building initial module for 2.6.35-5-generic

Error! Bad return status for module build on kernel: 2.6.35-5-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/ndiswrapper/1.56/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ndiswrapper-dkms.0.crash'
dpkg: error processing ndiswrapper-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10

anyone can give me some advice?
thank you

---

### Post by yoyu007 on 2010-06-23
find some post,but cant  solved

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568065](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568065)

---


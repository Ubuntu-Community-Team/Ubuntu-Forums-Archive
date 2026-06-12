---
title: "Unable to install lirc in mythbuntu-diskless"
date: 2011-08-23
forum: Multimedia Software
---

### Post by Ram-Z on 2011-08-23
Hi,

I have set up a mythbuntu-diskless following those guides:
[https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless](https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless)
[http://www.mythtv.org/wiki/User:Keithamus](http://www.mythtv.org/wiki/User:Keithamus)

But I am unable to install lirc on the diskless image. Here is how I tried so far:
On the Server:
```
$ sudo mount -t proc proc /opt/ltsp/amd64/proc
$ sudo chroot /opt/ltsp/amd64
# aptitude install lirc
```And the Output:
```
The following partially installed packages will be configured:
  lirc 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up lirc (0.8.7-0ubuntu4.1) ...   
reload: Unknown instance: 
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lirc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up lirc (0.8.7-0ubuntu4.1) ...
reload: Unknown instance: 
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lirc
```Am I doing something wrong? Or should I install lirc via ssh directly on the client?

Thanks

edit: forgot to mention... I'm running Natty x86_64 an both client and server

---

### Post by sdavids on 2011-12-07
I guess you've probably solved this or given up by now.... but I stumbled on this post as I had the same problem so for the record I hacked it by doing

chmod -x /sbin/udevd

in the chroot environment.  The problem is the install script gives up if it can't restart the serial port, which it can't in the chroot, but of course there's no need to.

Obviously 

chmod +x /sbin/udevd

when lirc is installed

I suspect the real fix lies in fixing the deb postinstall script.

---


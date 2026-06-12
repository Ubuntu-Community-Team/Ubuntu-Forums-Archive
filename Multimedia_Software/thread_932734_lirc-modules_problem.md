---
title: "lirc-modules problem"
date: 2008-09-28
forum: Multimedia Software
---

### Post by smi402 on 2008-09-28
I note that the archive for lirc-modules-source was updated on Sept 25 to:

**lirc-modules-source_0.8.3-0ubuntu2_all.deb**

and the previous 0ubuntu1 version deleted.

Whilst the previous version installed without any problems there appear to be problems installing the new 0ubuntu2 version on _amd64 installations that have dkms installed. I have no way of checking, but it is probably also a problem on _i386 installations.

```
frank@FWS64:~$ sudo dpkg -i lirc-modules-source_0.8.3-0ubuntu2_all.deb
Selecting previously deselected package lirc-modules-source.
(Reading database ... 147413 files and directories currently installed.)
Unpacking lirc-modules-source (from lirc-modules-source_0.8.3-0ubuntu2_all.deb) ...
Setting up lirc-modules-source (0.8.3-0ubuntu2) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of lirc_atiusb.ko failed for: 2.6.24-19-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.3/build/ for more information.
Installing initial module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.
You must run a dkms build for kernel 2.6.24-19-generic (x86_64) first.
Done.

```
This package is needed to get the IMON LCD devices to work. :(

---

### Post by odinb on 2008-09-29
Can confirm the same on i386:

```
brodersen@ubuntu-htpc:/usr/src$ sudo dpkg -i lirc-modules-source_0.8.3-0ubuntu2_all.deb
Selecting previously deselected package lirc-modules-source.
(Reading database ... 106984 files and directories currently installed.)
Unpacking lirc-modules-source (from lirc-modules-source_0.8.3-0ubuntu2_all.deb) ...
Setting up lirc-modules-source (0.8.3-0ubuntu2) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of lirc_atiusb.ko failed for: 2.6.24-19-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.3/build/ for more information.
Installing initial module

Error! Could not locate lirc_atiusb.ko for module lirc in the DKMS tree.
You must run a dkms build for kernel 2.6.24-19-generic (i686) first.
Done.
```


So what to do now?

---

### Post by smi402 on 2008-10-04
See Post 57 on thread 907256 for the 0ubunt1 version of these packages:

[http://ubuntuforums.org/showthread.php?t=907256&page=6]("http://ubuntuforums.org/showthread.php?t=907256&page=6")

Frank

---

### Post by odinb on 2008-10-09
Thanks Frank!

Sat up untill 3AM last night, and my remote _**and**_ LCD now works!

Best and easiest guide on this Antec Fusion Black case so far!

Works excellent in XBMC with my Harmony (using MCE-codes) almost out-of-the-box with just small adjustments on the remote side.

Works somewhat with Myth after adding the lircrc config file for MCE remote from here: [http://www.mythtv.org/wiki/index.php/MCE_Remote](http://www.mythtv.org/wiki/index.php/MCE_Remote)
Myth backend hogs the LCDd after mythfrontend has been active. Need to find out how to get it to restart LCDd when exiting mythfrontend so that other applications can use the LCD....kind of hard to do a "sudo /etc/init.d/LCDd restart" from the remote.

Great guide!!

Thanks, thanks and thanks!

---

### Post by MacLeod_1980 on 2009-02-10
I am not sure how you got this to work in the end.  I downloaded the information that is listed in post #57 of another topic - I placed them in /usr/src, but I am not sure what I have to do then.

If I try and install I get the same error...

FYI I am trying to follow this guide:

[http://xbmc.org/forum/showthread.php?t=40290](http://xbmc.org/forum/showthread.php?t=40290)

But having no luck at the:

sudo dpkg-reconfigure lirc-modules-source

section...

I am pretty new to linux, so any help would be much appreciated.

---


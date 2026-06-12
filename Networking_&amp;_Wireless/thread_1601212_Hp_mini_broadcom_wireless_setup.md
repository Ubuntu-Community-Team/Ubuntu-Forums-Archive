---
title: "Hp mini broadcom wireless setup"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by ali999 on 2010-10-19
Hi everyone,

I recently had to reinstall ubuntu netbook 10.04 on my comp after I messed it up accidently. Only problem is now I cant get my wireless driver to install. Previously I had access to a wired connection so it was easy to do, but unfortunately I don't have that anymore. I tried to follow the instructions here [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) but keep getting a message saying I need to insert CD-ROM with no workaround. Being a netbook, my ocmputer has no cd rom. How can I install the drivers off the USB? 

Thanks in advance.

---

### Post by P4man on 2010-10-20
You can download the .deb packages and put them on a usb stick, then just double click to install. Solving dependencies can be tricky (package A requiring package B which depends on C and D, so you need to get them all), but in this case it might be straightforward:

[http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source)

If you do need to install extra packages, the installer will tell you which ones, and you can grab them from the same site and you may need to install them all at once by running

```
sudo dpkg -i /path/to/your/usb/*.deb
```

---

### Post by ali999 on 2010-10-20
I tried the method above get this error. Not really sure what to make of it...any ideas?

```
(Reading database ... 117868 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu5 (using bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.1.1.2-2fakesync1 (using dkms_2.1.1.2-3ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from libc6-dev_2.12.1-0ubuntu6_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.35.22.23 (using linux-headers-generic_2.6.35.22.23_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.35-1022.33 (using linux-libc-dev_2.6.35-1022.35_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up dkms (2.1.1.2-3ubuntu1) ...
Installing new version of config file /etc/kernel/prerm.d/dkms ...
Installing new version of config file /etc/kernel/postinst.d/dkms ...
Installing new version of config file /etc/kernel/header_postinst.d/dkms ...
Setting up linux-headers-generic (2.6.35.22.23) ...
Setting up linux-libc-dev (2.6.35-1022.35) ...
Setting up libc6-dev (2.12.1-0ubuntu6) ...
Processing triggers for man-db ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/bcmwl-kernel-source.0.crash'
dpkg: error processing bcmwl-kernel-source (--install):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-sourc
```

---

### Post by ali999 on 2010-10-21
problem solved...turns out i was using the drivers for lucid and not meerkat

---

### Post by P4man on 2010-10-21
I linked to the ones for lucid, because thats what you said you were using :)

Anyway, please make the thread as [solved] in thread tools :)

---

### Post by Angelo Maldito on 2010-10-30
After several hours struggling to fix my wifi on my HP MINI 210, even  with broadcom sta driver enabled, wireless supposedly enabled (but with  the led light off and not able to see the available networks) I have  finally found the solution here:

[http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/](http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/)   (THANK YOU VERY MUCH DARKMOON !!!) 

The solution was simple, for whatever reason that I am not able to  understand, after you intall the drivers and everything else, THE BLOODY  THING COMES BLOCKED !!!

So in order to unblock, the goddamn thing just open a terminal, login as root ant type the following command:

rfkill unblock all


Thats is it, now its done, working perfectly !!!

I hope it save some hours for someone !

---

### Post by samo_ak47 on 2011-03-22
> **Angelo Maldito said:**
> After several hours struggling to fix my wifi on my HP MINI 210, even with broadcom sta driver enabled, wireless supposedly enabled (but with the led light off and not able to see the available networks) I have finally found the solution here:
 
[http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/](http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/) (THANK YOU VERY MUCH DARKMOON !!!) 
 
The solution was simple, for whatever reason that I am not able to understand, after you intall the drivers and everything else, THE BLOODY THING COMES BLOCKED !!!
 
So in order to unblock, the goddamn thing just open a terminal, login as root ant type the following command:
 
rfkill unblock all
 
 
Thats is it, now its done, working perfectly !!!
 
I hope it save some hours for someone !
 
Your a life saver thanks alot!!!! it did save me hours of troubles and i'm sure alot of other people whos got this laptop and intalled the latest updates!

---


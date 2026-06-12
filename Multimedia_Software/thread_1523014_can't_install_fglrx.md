---
title: "can't install fglrx"
date: 2010-07-03
forum: Multimedia Software
---

### Post by venicequeen7706 on 2010-07-03
i'm having the same issue as many people with ATI video cards and i have read installing fglrx from synaptic would fix the issue, but i can't get it to install. 

from synaptic it fails. 

using the command "sudo apt-get install i get the following result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B/23.5MB of archives.
After this operation, 70.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package fglrx.
(Reading database ... 181666 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.741-0ubuntu0sarvatt2~lucid_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.741-0ubuntu0sarvatt2~lucid_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up fglrx (2:8.741-0ubuntu0sarvatt2~lucid) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.741 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-23-generic
Building for architecture i686
Building initial module for 2.6.32-23-generic

Error! Bad return status for module build on kernel: 2.6.32-23-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.741/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


i tried going to System > Administration > Hardware Drivers and it told me there are no drivers.

someone gave me this link [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

the restricted drivers manager method doesn't find any drivers

the x team's ppa give me the following result:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring  --secret-keyring /etc/apt/secring.gpg --trustdb-name  /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg  --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com  --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error



installing drivers manually goes fine until the install .deb step where it gives me this result:
Building initial module for 2.6.32-23-generic

Error! Bad return status for module build on kernel: 2.6.32-23-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.741/build/ for more information.
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.741-0ubuntu1) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev



I'm completely lost on what to do here. any advice would be great. Thanks

---

### Post by Yellow Pasque on 2010-07-03
Post output of:
```
cat /var/lib/dkms/fglrx/8.741/build/make.log
```
Use [ code ][ /code ] blocks

---

### Post by venicequeen7706 on 2010-07-03
```
 cat /var/lib/dkms/fglrx/8.741/build/make.log
DKMS make.log for fglrx-8.741 for kernel 2.6.32-23-generic (i686)
Sat Jul  3 12:42:00 EDT 2010
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
Makefile:94: *** mixed implicit and normal rules.  Stop.
Makefile:94: *** mixed implicit and normal rules.  Stop.
build failed with return value 2 
```

---

### Post by Yellow Pasque on 2010-07-03
Are you using a non-standard compiler/gcc? [http://linux.derkeiler.com/Mailing-Lists/Debian/2005-02/3029.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-02/3029.html)
What is output of:
```
ls -la /usr/bin/gcc
```

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555957](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555957)

---

### Post by venicequeen7706 on 2010-07-03
i have no idea and i don't really understand this part:

So, I unlinked the symbolic link  
/usr/bin/gcc -> /usr/bin/builder-cc, and pointed gcc 
to /usr/bin/gcc-3.3.

---

### Post by Yellow Pasque on 2010-07-03
See my edit above.

---

### Post by venicequeen7706 on 2010-07-03
```
 ls -la /usr/bin/gcc
lrwxrwxrwx 1 root root 10 2010-04-24 13:25 /usr/bin/gcc -> builder-cc

```

---

### Post by Yellow Pasque on 2010-07-03
/usr/bin/gcc should point to /usr/bin/gcc-4.4 in lucid
```
cd /usr/bin
sudo rm gcc
sudo ln -s gcc-4.4 gcc
```

---

### Post by venicequeen7706 on 2010-07-03
ok it installed now, but at the configure step i get this result ```
 sudo aticonfig --initial -f
aticonfig: No supported adapters detected

```

---

### Post by venicequeen7706 on 2010-07-03
Also now comiz is behaving differently. my widget layer isn't working and it looks and acts like i have dekstop wall enabled but desktop cube is what i actually have enabled

---

### Post by Yellow Pasque on 2010-07-03
> aticonfig: No supported adapters detected
So what video card do you have? These should tell you:
```
lspci
sudo lshw -C video
```

---

### Post by venicequeen7706 on 2010-07-03
```
 
sudo lshw -c video
 *-display               
       description: VGA compatible controller
       product: M22 [Mobility Radeon X300]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:27 memory:c0000000-c7ffffff(prefetchable) ioport:2000(size=256) memory:c8400000-c840ffff memory:c8420000-c843ffff(prefetchable)

```

---

### Post by Yellow Pasque on 2010-07-03
Well, the proprietary drivers don't support that card (there's a big, red warning in the install guide).
Follow this to reset your video driver: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)
Also, put gcc link back the way it was (BTW, thanks for helping me find that bug):
```
sudo ln -sf /usr/bin/builder-cc /usr/bin/gcc
```

---

### Post by venicequeen7706 on 2010-07-03
wow, i'm embarrased. I read that warning too, but i misread it as if your card isn't on that list it isn't supported. thanks for all of your help

---


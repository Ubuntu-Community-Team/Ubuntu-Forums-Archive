---
title: "ATI Driver Installation Problem unter Ubuntu 8.10"
date: 2008-11-09
forum: Multimedia Software
---

### Post by Baender on 2008-11-09
I tried to install the graphic driver Catalyst 8.10 on Ubuntu 8.10.
But while the installation i got an error message in my console:

```
erik@erik-desktop:~$ sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb 
[sudo] password for erik: 
(Lese Datenbank ... 102393 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von xorg-driver-fglrx 2:8.542-0ubuntu1 (durch xorg-driver-fglrx_8.542-0ubuntu1_i386.deb) ...
Entpacke Ersatz für xorg-driver-fglrx ...
Vorbereiten zum Ersetzen von fglrx-kernel-source 2:8.542-0ubuntu1 (durch fglrx-kernel-source_8.542-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Entpacke Ersatz für fglrx-kernel-source ...
Vorbereiten zum Ersetzen von fglrx-amdcccle 2:8.542-0ubuntu1 (durch fglrx-amdcccle_8.542-0ubuntu1_i386.deb) ...
Entpacke Ersatz für fglrx-amdcccle ...
Richte fglrx-kernel-source ein (2:8.542-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.542/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (i686) first.
Done.

Richte xorg-driver-fglrx ein (2:8.542-0ubuntu1) ...

Verarbeite Trigger für man-db ...
Richte fglrx-amdcccle ein (2:8.542-0ubuntu1) ...
Verarbeite Trigger für libc6 ...
ldconfig deferred processing now taking place
erik@erik-desktop:~$ 


```

I took this installation guide helping me unter Ubuntu 8.04 too:
[Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

By tipping fglrxinfo into the console i dont get an ATI Driver output.

Does anyone have a solution for this problem?
Is it an Ubuntu 8.10 problem? Because unter Ubuntu 8.04 all works fine.

---

### Post by microft on 2008-11-09
I'm having the same problem with an HD4870.

Since 8.04 and 8.10 are using different versions of the kernel.... maybe that's the problem.

I was following this: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by Bablefish on 2008-11-09
Remember it's a double edge sword when installing ATI drivers. Meaning you have just as much as a chance that it will work for you as it also might crash your system.

---

### Post by microft on 2008-11-09
In my case the only problem is video flickering. Everything else seems to work fine.

If I disable Compiz, the video flickering stops... but I really like compiz...

For now I'll use x11 video output with VLC as a work around the problem.

---

### Post by Baender on 2008-11-10
Thank you for your answer. All woud be fine, if the driver installation under Ubuntu 8.04 won't success. But under Ubuntu 8.04 the whole installation works fine. I got a Radeon 2600 HD AGP Version, someone would call this a sticky graphic card for Ubuntu, but i works.
Only under Ubuntu 8.10 i got this message:
```

Error!  Build of fglrx.ko failed for: 2.6.27-7-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.542/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-7-generic (i686) first.

```
Maybe it helps by writing you my procedure.

First fo all i updated Ubuntu and installed following packages:
```
$ sudo apt-get update
$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) 
```
Then i created a .deb pack for starting the installation:
```
$ sh ati-driver-installer-8-10-x86.x86_64.run --buildpkg Ubuntu/hardy 
```
I skiped the 4. point and continued installing the driver
```
$ sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb 
```
I don't understand the note of the tuturial:
Starting from 8-10 version of the driver, installing the following package ensures compatibility with restricted drivers' manager:

Now i got the error message, i think this is the mainproblem, by proceeding the tuturial i wasn't able to get this driver work.

Does someone have an idea how to fix the error, maybe could fix a further ATI-Driver 8.11 this problem? Or is there an other way to install the new graphics driver.

---

### Post by microft on 2008-11-14
There is a new version of the ati driver. I haven't had the time to try the ati installer and there aren't any packages in the repositories yet.

for x86: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

for amd64: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

---


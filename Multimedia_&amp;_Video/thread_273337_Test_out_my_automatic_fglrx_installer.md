---
title: "Test out my automatic fglrx installer"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by kthakore on 2006-10-07
here it is [click here]("http://kartikhacked.blogspot.com/2006/10/for-all-ubuntu-users-out-there.html")

---

### Post by eson on 2006-10-08
do you have some more information. A simple guide how to do the install maby. I'll try to do the install now.

---

### Post by kthakore on 2006-10-08
Extract the flrxinstaller file, you will get a folder called fglrx 

Get the latest ati driver from: [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Select your ati driver type and install to the fglrx folder that you extracted

right click on the ati-driver-installer-X-XX-X.run and rename it to ati.run, and change the permissions to allow for your username execute for ati.run and fglrx file in the fglrx folder

run the ati by double clicking on it and choosing run in terminal 

follow the instructions

and the fglrx script by double clicking on it and choosing run in terminal

---

### Post by kthakore on 2006-10-08
I have gotten several downloads, can you just let me know how the script is, any problems, comments, critque?

---

### Post by kthakore on 2006-10-08
did it work for anyone yet? any error messages?

---

### Post by overide19 on 2006-10-14
not sure if its just me. but i dont think it worked....any help?





root@overide:/home/overide# /home/overide/fglrx/fglrx
What is the version of the driver, in this format 8.29.6-1.i386?
8.29.6-1.i686
dpkg: error processing xorg-driver-fglrx_8.29.6-1.i686.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.29.6-1.i686.deb
dpkg: error processing fglrx-kernel-source_8.29.6-1.i686.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx-kernel-source_8.29.6-1.i686.deb
dpkg: error processing fglrx-control_8.29.6-1.i686.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx-control_8.29.6-1.i686.deb
Getting source for kernel version: 2.6.15-27-686
Kernel headers available in /usr/src/linux

Done!

Updated infos about 69 packages
The source tarball could not be found!
Package fglrx-kernel-source not installed?
Running "m-a -f get fglrx-kernel-source" may help.
Done with /usr/src/fglrx-kernel-2.6.15-27-686_8.29.6-1+2.6.15-27.48_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.15-27-686.
(Reading database ... 90002 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.15-27-686 (from .../fglrx-kernel-2.6.15-27-686_8.29.6-1+2.6.15-27.48_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.15-27-686:
 fglrx-kernel-2.6.15-27-686 depends on xorg-driver-fglrx (= 8.29.6-1); however:
  Package xorg-driver-fglrx is not installed.
dpkg: error processing fglrx-kernel-2.6.15-27-686 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.15-27-686

I: Direct installation failed, trying to post-install the dependencies

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fglrx-kernel-2.6.15-27-686
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 553kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 90005 files and directories currently installed.)
Removing fglrx-kernel-2.6.15-27-686 ...
/home/overide/fglrx/fglrx: line 11: udo: command not found
Found fglrx primary device section
Nothing to do, terminating.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2
cp: cannot stat `libGL.so.1.2': No such file or directory

---

### Post by kthakore on 2006-10-29
oops there seems to be a mistake 

```
What is the version of the driver, in this format 8.29.6-1.i386?
```

should be

```
What is the version of the driver, in this format 8.29.6-1_i386?
```

also did you depackage the ati-driver-installer-X.XX.XX-x86.run file to get the binaries.

---


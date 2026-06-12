---
title: "SMART Board Notebook on 64-bit"
date: 2010-02-10
forum: Multimedia Software
---

### Post by clconway on 2010-02-10
(NOTE: This problem was previously discussed [here]("http://ubuntuforums.org/showthread.php?t=1055150"), but the thread is locked due to the closure of the 64-bit forum.)

I'm trying to figure out how to install the [SMART Notebook software]("http://www2.smarttech.com/st/en-US/Support/Downloads/SBS/NBS10Linux.htm") on 64-bit Ubuntu. The method described in [this blog post]("http://www.crucialthought.com/2009/08/05/how-to-install-smart-notebook-software-on-a-64-bit-ubuntu-machine/") fails for me:

```

$ linux32
$ sudo package install SMART\ Notebook\ Software\ With\ Drivers\ 10.package 
^[OF
# Preparing package: SMART Software                                             
# Checking for Glib Utility Library ... passed
# Checking for X ... passed
# Checking for Standard C++ library ... passed
# Checking for GTK+ user interface toolkit ... passed
# Checking for libXinerama.so ... 1.0.0
passed
# Checking for libXfixes.so.3 ... 3.1.0
passed
# Checking for libxkbfile.so ... failed
FAIL: Unable to prepare package SMART Software.

```

This situation persists even after using getlibs to install libxkbfile1 and libxkbfile-dev:

```

$ ls /usr/lib32/*xkb*
/usr/lib32/libxkbfile.a  /usr/lib32/libxkbfile.so  /usr/lib32/libxkbfile.so.1  /usr/lib32/libxkbfile.so.1.0.2

```

I have a different problem with the 9.6 version of the software:

```

$ linux32
$ sudo package install "SMART Board Software 9.7.68.0.package"

# Preparing package: SMART Board Software                                                                                                                                                      
# Checking for required C library versions ... failed
# FAIL: 
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
# 
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
# 
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL: Unable to prepare package SMART Board Software.

```

I have libc6-i386 version 2.10.1-0ubuntu16, installed via ia32-libs version 2.7ubuntu17.

Has anybody gotten this software working on 64-bit? If so, how?

---

### Post by Stuart42 on 2010-03-25
I'm having an identical issue...

:-(

---

### Post by acermobile on 2010-05-28
Proceed as follows:

Goto [http://www.autopackage.org/download-tools.html](http://www.autopackage.org/download-tools.html)
Download the new version, untar and run "linux32 ./install" in the directory. Then confirm the next question with yes and use this new version which will work smoothly with the SMART Software.

Hope this is of help - I got almost mad trying to get the thing installed...

---

### Post by clconway on 2010-05-28
acermobile, For me, this makes the last problem go away, but introduces a new one. I downloaded autopackage.tar.bz2 from your link and installed it, then did the following:

```
$ sudo linux32 package install -t SMART\ Notebook\ Software\ With\ Drivers\ 10.package 

# Preparing package: SMART Software                                                                                                                                                            
# Checking for Glib Utility Library ... passed
# Checking for X ... passed
# Checking for Standard C++ library ... passed
# Checking for GTK+ user interface toolkit ... passed
# Checking for libXinerama.so ... 1.0.0
passed
# Checking for libXfixes.so.3 ... 3.1.0
passed
# Checking for libxkbfile.so ... 1.0.2
passed
# Checking for 2.6.x Kernel ... passed
# Checking for SMART Install Frontend ... passed   
## Preparing package: SMART Install Frontend                                                                                                                                                   
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for Common files for SMART Software ... passed   
## Preparing package: Common files for SMART Software                                                                                                                                          
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for SMART Product Update ... passed   
## Preparing package: SMART Product Update                                                                                                                                                     
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for SMART Language Setup ... passed   
## Preparing package: SMART Language Setup                                                                                                                                                     
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for SMART Board Drivers ... passed   
## Preparing package: SMART Board Drivers                                                                                                                                                      
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for SMART Gallery Setup ... passed   
## Preparing package: SMART Gallery Setup                                                                                                                                                      
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for SMART Activation Wizard ... passed   
## Preparing package: SMART Activation Wizard                                                                                                                                                  
## Checking for required C library versions ... passed   
# Preparing package: SMART Software                                                                                                                                                            
# Checking for SMART Notebook Software ... passed   
## Preparing package: SMART Notebook Software                                                                                                                                                  
## Checking for required C library versions ... passed   
# Installing package: SMART Install Frontend (package 1 of 9)                                                                                                                                  
# 100%[==================================================] Extracting
# Preparing executables...
# Updating package database...
# Installing package: Common files for SMART Software (package 2 of 9)                                                                                                                         
# 100%[==================================================] Extracting
# Preparing executables...
# Copying files to /opt/SMART Technologies/common/lib/.
# 100%[==================================================] Copying
# Copying files to /opt/SMART Technologies/common/plugins/imageformats
# 100%[==================================================] Copying
# Copying files to /opt/SMART Technologies/common/xdg/.
# Updating package database...
# Installing package: SMART Product Update (package 3 of 9)                                                                                                                                    
# 100%[==================================================] Extracting
# Preparing executables...
# Copying files to /opt/SMART Technologies/Product Update/bin
# 100%[==================================================] Copying
Exit code is: 1. Rolling back dependencies for @smarttech.com/SPU:3.1.116.0
FAIL: Package SMART Product Update could not be installed.
chris@firefly:~/Tools/SMART Notebook Software With Drivers 10$ wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.
wget: --cache: Invalid boolean `off --continue --tries=2 --timeout=12'; use `on' or `off'.

```

No idea where the wget's are coming from. Autopackage seems to be ignoring the autopackage_wget_options setting in /etc/autopackage/config.

---


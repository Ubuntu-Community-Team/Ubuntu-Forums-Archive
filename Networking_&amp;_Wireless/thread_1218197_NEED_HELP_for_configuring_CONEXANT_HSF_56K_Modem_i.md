---
title: "NEED HELP for configuring CONEXANT HSF 56K Modem in Jaunty 9.04"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by James@Brunei on 2009-07-20
Dear freinds, 

I am a new user in ubuntu 9.04. I got following problems in my ubuntu for internet connection,


**1.** My Modem details as follows scanned by LsitModem App.

MODEM #1: 
      PCI CONFIGURATION INFORMATION READ: 
      VENDOR ID         : 14F1 
      DEVICE ID         : 2F30 
      SUBVENDOR ID    : 14F1 
      SUBDEVICE ID     : 205D 
      REVISION ID                : 01 

DEDUCED INFORMATION: 
      VENDOR NAME       : CONEXANT 
 
C.COM/ 
      MODEM TYPE     : HSF 
      WINXP INBUILD SUPPORT   : NO 



**2. **Based on this details I try to install,  "hsfmodem_7.80.02.04full_k2.6.28_11_generic_ubuntu_i386.deb" from Linuxant web site but I got a error message of dependencies (alsa-driver). Then I installed "alsa-driver-linuxant_1.0.20.3_k2.6.28_11_generic_ubuntu_i386.deb" then I complete installation of "hsfmodem_7.80.02.04full_k2.6.28_11_generic_ubuntu_i386.deb" and did configuring.  Then I try to connect to internet with network admin tool but unfortunately i cant get connection.


**3. **Then I look for help and recently I came to know that dell supporting CONEXANT HSF modem driver (from ubuntu website), I removed above HSF driver files and installed "hsfmodem-7.80.02.03full_Jaunty.tar.bz2" and did hsfconfig but still I cant get connection to internet.


I request ubuntu friends to help me to solve this issue. 

Thank you

Best regards
James

---

### Post by HotShotDJ on 2009-08-20
Don't use hsfmodem-7.80.02.03full_Jaunty.tar.bz2.  Follow the section titled "Building latest hsfmodem driver + free & full-speed Dell binaries" on the following page: [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

I've used it on both the standard kernels supplied in Jaunty as well as the 2.6.30 series and it works perfectly.

In addition to the build-essential and linux-headers packages which you will need to install before following the instructions (you may very well have already installed those two), I strongly recommend that you install the checkinstall package.  Then, for step #5, replace "sudo make install" with "sudo checkinstall" -- just accept the defaults when it runs.  This will create (and install) a deb package for you... it will make removing the package much easier down the road.

When you update your kernels, you'll want to run "sudo dpkg -r hsfmodem" (this will only work if you followed my advise and used checkinstall to compile and install hsfmodem) before rebooting to the new kernel or you will run into problems upon reboot.  Once booted to the new kernel, reinstall alsa-driver-linuxant (either by downloading a new precompiled version for your new kernel or using the generic version, which will compile itself for your kernel) then redo step #5.

---

### Post by Willn21 on 2009-08-20
I followed the guide and on the first step I had a problem

I tried to install the alsa-driver-linuxant_1.0.20.3_all.deb

and I got this error

```
root@ubuntu:/var/www# dpkg -i alsa-driver-linuxant_1.0.20.3_all.deb
(Reading database ... 44863 files and directories currently installed.)
Preparing to replace alsa-driver-linuxant 1.0.20.3 (using alsa-driver-linuxant_1.0.20.3_all.deb) ...
Unpacking replacement alsa-driver-linuxant ...
Setting up alsa-driver-linuxant (1.0.20.3) ...
Building modules for the 2.6.28-11-server kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.7610.log
dpkg: error processing alsa-driver-linuxant (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-driver-linuxant
```

before I got this error

```
dependency problems - leaving unconfigured
```

---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> I followed the guide and on the first step I had a problem

I tried to install the alsa-driver-linuxant_1.0.20.3_all.deb

and I got this error```

ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.7610.log
```

before I got this error

```
dependency problems - leaving unconfigured
```Have you looked at /tmp/alsa-driver-linuxant.7610.log?  Without that information, I can only guess at what the trouble might be.  But the most common issue with this type of package is not having the packages needed to compile the code installed.  That is easy enough to check:```
sudo apt-get install build-essential linux-headers-`uname -r` checkinstall
```If you still have trouble after that, please post the log file listed above and I'll see if we can get the problem sorted.

---

### Post by Willn21 on 2009-08-21
OK I installed those things and it went smoothly
but i still get an error
Here is my log:
> rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with kernel source... ./configure: line 4710: cd: /usr/src/linux: No such file or directory
/usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

---

### Post by Willn21 on 2009-08-21
bump

---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> OK I installed those things and it went smoothly
but i still get an error
Here is my log:Note the final line in the log.  This suggests that you have not yet installed some important packages.  Open up a terminal (Applications --> Accessories --> Terminal) and then run the following -- you can cut and paste it into the terminal:```
sudo apt-get install build-essential linux-headers-`uname -r` checkinstall
```Once these packages have been successfully installed (let me know if you get any errors), you should be able to get alsa-driver-linuxant and the modem drivers installed properly.

---

### Post by Willn21 on 2009-08-21
OK I will try that. by the way I am using ubuntu server not desktop

---

### Post by Willn21 on 2009-08-21
OK I just did a clean install of ubuntu and I typed this in
> sudo apt-get install build-essential linux-headers-`uname -r` checkinstallThen I did
```
 wget http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip
  unzip *.zip
  sudo dpkg -i alsa-driver-linuxant_1.0.20.3_all.deb
```Now it is stuck on this :
```
Building modules for the 2.6.28-11-server kernel, please wait...
```I've been waiting for 15 minutes now

---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> I've been waiting for 15 minutes nowKeep waiting.  It takes quite some time.  It is actually compiling the source code before installing.

---

### Post by Willn21 on 2009-08-21
Woot It worked.
New Problem:
When I did hsfconfig This is what happened:
```
hsfconfig
-bash: /usr/sbin/hsfconfig: Permission denied
david@ubuntu:~/hsfmodem-7.80.02.04full$ sudo hsfconfig
Conexant HSF softmodem driver, version 7.68.00.09oem

If you need assistance or more information, please go to:
        [http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Ubuntu-9.04 linux-2.6.28-11-server i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.28-11-server/build]

Building modules for kernel 2.6.28-11-server, using source directory
/lib/modules/2.6.28-11-server/build. Please wait...

ERROR: Module build failed!
Please examine the log file "/etc/hsfmodem/log/buildlog-20090821164138.txt" to determine why.
```Here is my log:
```
driver version 7.68.00.09oem
(cd /lib/modules/2.6.28-11-server/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-server/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
(cd /lib/modules/2.6.28-11-server/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-server/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.28-11-server/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.28-11-server/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-server/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-server'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-server'
make: *** [all] Error 2

```

---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> /usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
Yup.  The string.h error.  As per the trouble-shooting section of the installation how-to:

```
cd hsfmodem-7.80.02.04full
gedit modules/imported/include/osservices.h
```

Then, on line 356, change string.h to linux/string.h Then reinstall and recompile driver:```
sudo checkinstall && sudo hsfconfig
```

---

### Post by Willn21 on 2009-08-21
I changed string.h in 356 of /usr/lib/hsfmodem/modules/imported/include/osservices.h to linux/string.h and saved it

Then I ran > sudo checkinstall && sudo hsfconfig
Output:
> sudo checkinstall && sudo hsfconfig

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

*** No known documentation files were found. The new package
*** won't include a documentation directory.

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ hsfmodemyo ]
2 -  Name:    [ david ]
3 -  Version: [ 20090821 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ david ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ david ]

Enter a number to change any of them or press ENTER to continue:

Installing with make...Installing with install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> I changed string.h in 356 of /usr/lib/hsfmodem/modules/imported/include/osservices.h to linux/string.h and saved it...Thats not the file I told you to edit... but it should work nonetheless.

Anyway, the reason you got the error is that you were not in the right directory.  Make sure that you cd to hsfmodem-7.80.02.04full first, then run```
sudo checkinstall && sudo hsfconfig
```

EDIT:  Hold up -- if you run checkinstall again, it will mess up the edits you made to /user/lib/hsfmodem/modules/imported/include/osservices.h

Since you edited that file, rather than the one I suggested, you should NOT run checkinstall again... just sudo hsfconfig.  However, you might run into trouble down the line if you don't make the correction in the hsfmodem-7.80.02.04full/modules/imported/include/osservices.h file instead of /usr/lib... (in which case, you DO want to run sudo checkinstall && sudo hsfconfig)

---

### Post by Willn21 on 2009-08-21
I my fault.  I didn't realize we were going to compile those files again.  I thought you wanted me to edit the other ones.  I am doing it now.  I will let you know how it works

---

### Post by Willn21 on 2009-08-21
Wow, Thanks a lot. It worked. I installed hylafax and configured it. when I do faxstat it shows the modem.  Now I just want to get it to save the faxes.  you wouldn't know how to do that? would you?

---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> Now I just want to get it to save the faxes.  you wouldn't know how to do that? would you?I know absolutely nothing about hylafax.  Efax-gtk is much simpler and saves faxes automatically in ~/faxin. But since you seem to be setting up a server, hylafax may be the better option.  You probably need to start a new thread for that.

EDIT: OH... almost forgot... open System --> Administration --> Hardware Drivers to make sure that your shiny new driver is activated.

EDIT 2:  Hmmmm... I keep forgetting that you are using Ubuntu Server... my first edit might not apply to you.

---

### Post by Willn21 on 2009-08-21
ok sure thing. thanks again. tell me if there is anything i can do for you

---

### Post by HotShotDJ on 2009-08-21
> **Willn21 said:**
> tell me if there is anything i can do for youNext time you're in the Hartford, Connecticut area, you can buy me a drink. :)  Yes, sad but true, I work for Beer.

---

### Post by HotShotDJ on 2009-08-21
Just some final notes:  I said earlier in the thread that you will need to uninstall hsfmodem when you upgrade your kernel.  The more I think about it, the more I'm almost sure that this is not true.

Upon your first boot with a new kernel, the system will attempt (and fail) to build and start the hsfmodem module for the new kernel.  I THINK all you need to do is reinstall alsa-driver-linuxant and then run "sudo hsfconfig" to get it working after a kernel upgrade.

---

### Post by Willn21 on 2009-08-21
note taken

---

### Post by Fitch on 2010-01-07
Hi there, thought I'd annoy you and show you my log, probably not quite the same as above, but here goes anyway.
Installed as suggested (even though I have Karmic) and sudo make install went fine.

sudo /usr/sbin/hsfconfig not so well.

ERROR: Module build failed!
Please examine the log file "/etc/hsfmodem/log/buildlog-20100108010057.txt" to determine why.

The log file shows:

driver version 7.68.00.09oem
(cd /lib/modules/2.6.31-17-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-17-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
(cd /lib/modules/2.6.31-17-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-17-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.31-17-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.31-17-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-17-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from <command-line>:0:
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:244:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:265:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:286:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:304:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:322:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:343:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:366:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:388:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:406:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:425:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:447:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:469:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:490:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:508:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:526:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:548:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:570:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:593:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:614:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:645:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:667:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:688:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:712:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:736:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:757:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [all] Error 2

So it looks like we have to pay our 20 bucks after all!
(well, actually, I was going to, but theirs didn't work either in that Efax went a little wierd, so I didn't buy it)

---

### Post by alexfish on 2010-01-07
Hi

 this may or may not help 


[LIST]
[*][SIZE=2][COLOR=Blue][Other Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#softmodem")[/COLOR][/SIZE]
[LIST]
[*][SIZE=2][COLOR=Blue][Conexant Soft Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#softmodem")[/COLOR][/SIZE]
[/LIST]
[/LIST]

---

### Post by alexfish on 2010-01-08
**Conexant/Rockwell modem HOWTO**

**Imran Ghory**

[EMAIL="ImranG@btinternet.com"]ImranG@btinternet.com[/EMAIL]



2001-08-01

[B]Revision History

[/B]Revision 1.32002-03-12Revised by: ig

Updated to deal with new HCF driver.


Revision 1.22002-02-21
Revised by: igUpdated to deal with new HSF driver and release date for HCF driver.

Revision 1.02001-09-09
Revised by: igAdded entries to the FAQ, corrected grammatical errors, and update a URL.

Revision 0.92001-08-01
Revised by: igInitial release.

 A guide to using Conexant and Rockwell chipset based Software modems under Linux. 



**Table of Contents**1. [Introduction]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#INTRODUCTION")
1.1. [Purpose of the howto]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#PURPOSE")
1.2. [About the howto]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#ABOUT")
1.3. [Feedback]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FEEDBACK")
1.4. [License]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#LICENCE")
1.5. [Acknowledgments]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#ACKNOWLEDGEMENTS")
1.6. [Getting Help]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#GETTING-HELP")

2. [Quick Start guide]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#QUICK-START")
2.1. [Quick Starting with an HCF modem]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#QUICK-START-HCF")

3. [Identifying your modem type]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#GETTING-STARTED")

4. [HCF chipset based modems]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HCF")
4.1. [History]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HCF-HISTORY")
4.2. [Miscellaneous information]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#MISC-HCF")

5. [HSF]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HSF")
5.1. [History]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#HSF-HISTORY")
5.2. [Kernel 2.2.14 - 18]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#KERNEL14-18")
5.3. [Kernel 2.4.*]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#KERNEL4-SERIES")
5.4. [Troubleshooting FAQ]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FAQ")

A. [License]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FDL-APP").1. [GNU Free Documentation License]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html#FDL")
[]("http://www.faqs.org/docs/Linux-HOWTO/Conexant+Rockwell-modem-HOWTO.html")

---

### Post by Fitch on 2010-01-08
Since writing this, I upgraded to 9.10
The kernel for Karmic is 2.6.31-17, as yet there is nothing for that kernel.
I will re-install the linmodem as suggested earlier and see if I can go from there.

---

### Post by Fitch on 2010-01-08
AHA!
post#10 in
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308328](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308328) 
did it for me

---


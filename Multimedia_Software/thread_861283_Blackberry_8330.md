---
title: "Blackberry 8330"
date: 2008-07-16
forum: Multimedia Software
---

### Post by metallica1973 on 2008-07-16
Does Ubuntu have a package that will work with the Blackberry 8330? I have been using Mandriva Spring 2008 and it does work all that great. Thanks

---

### Post by pvalley1967 on 2008-07-16
Please Check Synaptic with the file name also what is the package name? I own a 8100 perl

need my crack crack berry need it:))

---

### Post by metallica1973 on 2008-11-07
I check synaptic and I could not find a package for the Blackberry. help?

---

### Post by reg-sux on 2008-11-11
Although there isn't a package on the repositories, you can check [barry]("http://netdirect.ca/software/packages/barry/install.php"). It has binary packages for Ubuntu.

---

### Post by metallica1973 on 2008-11-14
When I try and compile barry like:

[PHP] ./buildgen.sh 
configure.ac: 8: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
automake: configure.ac: installing `./install-sh'
automake: configure.ac: installing `./missing'
configure.ac: 8: required file `./config.h.in]' not found
Makefile.am:17: variable `subdirs' not defined
src/Makefile.am:38: WITH_GCCVISIBILITY does not appear in AM_CONDITIONAL
src/Makefile.am:35: AM_CFLAGS defined both conditionally and unconditionally
src/Makefile.am:36: AM_CXXFLAGS defined both conditionally and unconditionally
src/Makefile.am:37: AM_LDFLAGS defined both conditionally and unconditionally
src/Makefile.am:140: variable `LTLIBOBJS' not defined
src/Makefile.am:37: invalid unused variable name: `AM_LDFLAGS'
tools/Makefile.am:9: WITH_BOOST does not appear in AM_CONDITIONAL
tools/Makefile.am:8: bin_PROGRAMS defined both conditionally and unconditionally
tools/Makefile.am:16: WITH_BOOST does not appear in AM_CONDITIONAL
tools/Makefile.am:17: WITH_BOOST_PATHS does not appear in AM_CONDITIONAL
tools/Makefile.am:15: btool_LDADD defined both conditionally and unconditionally
tools/Makefile.am:26: WITH_BOOST does not appear in AM_CONDITIONAL
tools/Makefile.am:29: WITH_BOOST_PATHS does not appear in AM_CONDITIONAL
Putting files in AC_CONFIG_AUX_DIR, `..'.
configure.ac: 8: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
configure.ac: 8: required file `./config.h.in]' not found
src/Makefile.am:9: invalid variable `dist_glade_DATA'
Putting files in AC_CONFIG_AUX_DIR, `..'.
configure.ac: 7: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
src/Makefile.am:12: WITH_GCCVISIBILITY does not appear in AM_CONDITIONAL
src/Makefile.am:9: AM_CFLAGS defined both conditionally and unconditionally
src/Makefile.am:10: AM_CXXFLAGS defined both conditionally and unconditionally
src/Makefile.am:11: AM_LDFLAGS defined both conditionally and unconditionally
src/Makefile.am:22: invalid variable `dist_config_DATA'
src/Makefile.am:11: invalid unused variable name: `AM_LDFLAGS'
[/PHP]

I get this error message. I have installed all the dependencies and I cannot get past this point.

---

### Post by Mr_bleu on 2009-03-14
Anyone find a single, all encompassing deb file?  I'm getting frustrated trying to install all the correct dependencies and individual debs.

djr@popeye-laptop:/usr/bin$ btool -t
btool: error while loading shared libraries: libbarry.so.0: cannot open shared object file: No such file or directory
djr@popeye-laptop:/usr/bin$ cd ~/Desktop
djr@popeye-laptop:~/Desktop$ sudo dpkg -i --force-architecture libbarry.deb
dpkg: status database area is locked by another process
djr@popeye-laptop:~/Desktop$ sudo dpkg -i --force-architecture libbarry.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg - warning: downgrading libbarry0 from 0.14-2 to 0.14-0.
(Reading database ... 166089 files and directories currently installed.)
Preparing to replace libbarry0 0.14-2 (using libbarry.deb) ...
Unpacking replacement libbarry0 ...
Setting up libbarry0 (0.14-0) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
djr@popeye-laptop:~/Desktop$ cd /usr/bin
djr@popeye-laptop:/usr/bin$ barrybackup
barrybackup: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory
djr@popeye-laptop:/usr/bin$ sudo apt-get install libglademm-2.4.so.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglademm-2.4.so.1
djr@popeye-laptop:/usr/bin$ barrybackup
barrybackup: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory
djr@popeye-laptop:/usr/bin$ ./barrybackup
./barrybackup: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory
djr@popeye-laptop:/usr/bin$ cd ~/Desktop
djr@popeye-laptop:~/Desktop$ sudo dpkg -i --force-architecture barrydev.deb
dpkg: status database area is locked by another process
djr@popeye-laptop:~/Desktop$ sudo dpkg -i --force-architecture barrydev.deb
dpkg: error processing barrydev.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 barrydev.deb
djr@popeye-laptop:~/Desktop$ sudo dpkg -i --force-architecture barrydeb.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package libbarry-dev.
(Reading database ... 166172 files and directories currently installed.)
Unpacking libbarry-dev (from barrydeb.deb) ...
dpkg: dependency problems prevent configuration of libbarry-dev:
 libbarry-dev depends on libusb-dev; however:
  Package libusb-dev is not installed.
dpkg: error processing libbarry-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbarry-dev
djr@popeye-laptop:~/Desktop$

---

### Post by uMuppet on 2009-07-12
I agree, I've been going in circles trying to get all the dependencies together and just cannot get it to install.  

```
sudo dpkg -i barrybackup-gui_0.14-0_ubuntu804_i386.deb 
Selecting previously deselected package barrybackup-gui.
(Reading database ... 150583 files and directories currently installed.)
Unpacking barrybackup-gui (from barrybackup-gui_0.14-0_ubuntu804_i386.deb) ...
dpkg: dependency problems prevent configuration of barrybackup-gui:
 barrybackup-gui depends on libbarry0; however:
  Package libbarry0 is not installed.
dpkg: error processing barrybackup-gui (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 barrybackup-gui
```

Anyone?

---


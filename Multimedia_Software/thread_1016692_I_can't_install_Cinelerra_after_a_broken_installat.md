---
title: "I can't install Cinelerra after a broken installation"
date: 2008-12-20
forum: Multimedia Software
---

### Post by hijrakom on 2008-12-20
Hi!
I was trying to install cinelerra from debian-multimedia repository and in the middle of the Download I cancel the installation but the synaptic package manager continue anyway to install the half package .
after I removed the broken installation ,trying to reinstall cinelerra this time from akirad repository I got an error :

> matador810@matador810-desktop:~$ sudo aptitude install cinelerra
[sudo] password for matador810: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  cinelerra cinelerracv{a} libguicastcv{a} libmpeg3cv{a} libquicktimecv{a} 
  optlibx11-noxcb-6{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.0MB of archives. After unpacking 29.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package optlibx11-noxcb-6.
(Reading database ... 180211 files and directories currently installed.)
Unpacking optlibx11-noxcb-6 (from .../optlibx11-noxcb-6_2%3a1.1.3-1akirad1_i386.deb) ...
Selecting previously deselected package libguicastcv.
Unpacking libguicastcv (from .../libguicastcv_2.1.0-git20081029akirad3_i386.deb) ...
Selecting previously deselected package libmpeg3cv.
Unpacking libmpeg3cv (from .../libmpeg3cv_2.1.0-git20081029akirad3_i386.deb) ...
Selecting previously deselected package libquicktimecv.
Unpacking libquicktimecv (from .../libquicktimecv_2.1.0-git20081029akirad3_i386.deb) ...
Unpacking cinelerracv (from .../cinelerracv_2.1.0-git20081029akirad3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/cinelerracv_2.1.0-git20081029akirad3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/cinelerra/fonts/fonts.dir', which is also in package cinelerra-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_1%3a2.1.0-1svn20081017akirad2_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/cinelerracv_2.1.0-git20081029akirad3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of cinelerra:
 cinelerra depends on cinelerracv | cinelerrahv; however:
  Package cinelerracv is not installed.
  Package cinelerrahv is not installed.
dpkg: error processing cinelerra (--configure):
 dependency problems - leaving unconfigured
Setting up libmpeg3cv (2.1.0-git20081029akirad3) ...

Setting up libguicastcv (2.1.0-git20081029akirad3) ...

Setting up optlibx11-noxcb-6 (2:1.1.3-1akirad1) ...

Setting up libquicktimecv (2.1.0-git20081029akirad3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cinelerra
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 1 broken [+1].
please any idea..?:)

---


---
title: "I cannot install Realproducer 11 on Xubuntu Gutsy!!!"
date: 2007-10-26
forum: Multimedia Production
---

### Post by fitlad on 2007-10-26
I'm currently running Xubuntu Gutsy and I've tried to install Realproducer 11 from source package tgz. 
[http://www.realnetworks.com/products/producer/index.html](http://www.realnetworks.com/products/producer/index.html)
I searched the internet for the proper way to install this software and I found these links
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRealVideoStreaming.html#REALPRODUCER](http://www.yolinux.com/TUTORIALS/LinuxTutorialRealVideoStreaming.html#REALPRODUCER)
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
I ran terminal and typed the foloowing commands:
[PHP]cd /home/enduser/Packages/realproducer_basic_111_linux_setup
sudo auto-apt run ./configure
make
sudo checkinstall[/PHP]
 
However, the installation has failed :( :( :( and I got the following messages:
[PHP]enduser@Xubuntu:~/Packages/realproducer_basic_111_linux_setup$ sudo auto-apt run ./configure
[sudo] password for enduser:
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
E: Exec ./configure failed, auto-apt failed
enduser@Xubuntu:~/Packages/realproducer_basic_111_linux_setup$ make
make: *** No targets specified and no makefile found. Stop.
enduser@Xubuntu:~/Packages/realproducer_basic_111_linux_setup$ sudo checkinstall
 
checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Realproducer11
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "realproducer_basic_111_linux_setup" contains illegal.
*** Warning: characters. dpkg might not like that so I changed
*** Warning: them to dashes.

This package will be built according to these values: 

0 -  Maintainer: [ root@Xubuntu ]
1 -  Summary: [ Realproducer11 ]
2 -  Name:    [ realproducer-basic-111-linux-setup ]
3 -  Version: [ 20071026 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ realproducer_basic_111_linux_setup ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

enduser@Xubuntu:~/Packages/realproducer_basic_111_linux_setup$ [/PHP]

Can anyone help me to install Realproducer 11 on my machine? Any assistance is appreciated. :confused::confused::confused: Thanx

---

### Post by dschaller on 2008-05-11
Check my post on this thread:
[http://ubuntuforums.org/showthread.php?t=660838](http://ubuntuforums.org/showthread.php?t=660838)

I have RealProducer 11 Basic working on Ubuntu Gutsy.

---


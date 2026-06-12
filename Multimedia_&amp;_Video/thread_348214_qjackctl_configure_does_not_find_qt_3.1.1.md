---
title: "qjackctl configure does not find qt 3.1.1"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by DonQuichotte on 2007-01-28
Hey guys!


I'm relatively new to linux, and I've been trying to transform my laptop into a sound recoding workstation lately.

:guitar: 

I'm using a firewire audio interface (Edirol FA-101) and I can proudly say that after 4 days of hard building and installation work, my freebob driver recognized my device.

Now I am apparently incapable of loading the freebobdriver with the version of qjackctl that comes with apt-get. (0.2.20)

Version 0.2.21 of qjackctl is said to have support for freebob. Unfortunately, I have not been able to successfully compile qjackctl. I have installed everything I could find with the name "qt" in it in apt-get. I've even been to the Trolltech homepage and have downloaded, built and installed the very, very very very latest version of it. 


The message I'm getting is the following:

[quote=evil finite state machine]root@jony-laptop:~/downloads/qjackctl-0.2.21# ./configure --prefix=/usr/
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking whether QTDIR environment variable is set... /usr/include/qt4:/usr/share/qt4:/usr/include/qt3:/usr/share/qt3
checking for main in -lqt-mt... yes
checking for Qt library version >= 3.1.1... no; Qt 3.1.1 or greater is required
[/quote]

I can safely say that I DO have installed a version greater than 3.1.1.

Has anyone ever experienced similar problems? Could someone help me?

I've been searching teh intornets all day and I haven't been able to find any help whatsoever.

Every hint is greatly appreciated. Of course, you guys will be rewarded with recordings as soon as my recording setup is working.

Thanks in advance!

post scriptum: I'm sorry for crossposting, I just noticed that I had posted the original thread in an inappropriate forum.


DonQuichotte

---


---
title: "[SOLVED] Install AACGAIN on Hardy Running on AMD64"
date: 2008-10-22
forum: Multimedia Software
---

### Post by jezzabart on 2008-10-22
Please can anyone tell a complete newbie how to install AACGAIN on Ubuntu Hardy Heron on an AMD64 processor?

What file do I need to download and where from and exactly what do I need to do with it to install AACGAIN?

The more detail, the better, the only thing you don't need to bother writing is "Press Enter"!

---

### Post by jezzabart on 2008-10-24
I received the following solution which worked perfectly from the guy who runs this site: 

[http://jopsen.dk/en/Mainpage](http://jopsen.dk/en/Mainpage)

You can find the ACCGAIN source here: [http://altosdesign.com/aacgain/](http://altosdesign.com/aacgain/)
direct download link:
[http://altosdesign.com/aacgain/aacgain-1.7.tar.bz2](http://altosdesign.com/aacgain/aacgain-1.7.tar.bz2)

This is a source package you need to unpack it and compile it...
First unpack it by rightcliking it choosing unpack here...
Then open a terminal, navigate to the unpacked directory... e.g. cd "/home/..../accgain-1.7/"
then run ./configure
This configures the source code, and possibly complains about missing dependencies, these can be found in synaptic... Install missing dependencies and keep running ./configure untill all dependencies have been installed and configureation have succeeded... Then run make this builds/compiles the code... Once that's done... type sudo make install
this installs the compiled source...

---


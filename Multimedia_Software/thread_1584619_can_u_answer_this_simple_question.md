---
title: "can u answer this simple question??"
date: 2010-09-29
forum: Multimedia Software
---

### Post by avengerxp on 2010-09-29
well, i was trying to install GIMP, VLC player on ubuntu 10.04.1LTS, via the software center.

it gives me this error, how to fix this??

---

### Post by oldos2er on 2010-09-29
You're missing the GPG key for a repository; click 'Details' and it should tell you which one. [https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

### Post by avengerxp on 2010-09-30
yes it gives me this when i try to install VLC player.

libass4 libcddb2 libdca0 libdvbpsi5 libebml0 libenca0 libfaad2 libiso9660-7 liblua5.1-0 libmatroska0 libmodplug0c2 libmpcdec3 libsdl-image1.2 libtar libupnp3 libvcdinfo0 libvlc2 libvlccore2 libx264-85 libxcb-keysyms1 vlc vlc-data vlc-nox vlc-plugin-pulse


could you please assist me in resolving this. 

thanks in advance

---

### Post by oldos2er on 2010-09-30
Please post the full terminal output if there are errors. All I see is a list of vlc and its dependencies.

---

### Post by avengerxp on 2010-09-30
thanks for the reply, i managed to get it installed using synaptic package manager, ( i wonder why they added a software center, when this synaptic package manager is there). it warned me of unauthorized packages but allowed me to install.

if you dont mind me troubling you, can you have a look at this issue

[http://ubuntuforums.org/showthread.php?t=1583872](http://ubuntuforums.org/showthread.php?t=1583872)

i cant manage to play a movie in a good way without the drivers. (they seem to be like slideshows on screen)

---

### Post by Yellow Pasque on 2010-09-30
> **avengerxp said:**
> thanks for the reply, i managed to get it installed using synaptic package manager, ( i wonder why they added a software center, when this synaptic package manager is there). it warned me of unauthorized packages but allowed me to install.

if you dont mind me troubling you, can you have a look at this issue

[http://ubuntuforums.org/showthread.php?t=1583872](http://ubuntuforums.org/showthread.php?t=1583872)

i cant manage to play a movie in a good way without the drivers. (they seem to be like slideshows on screen)
Since you tried to install Catalyst, it may have screwed up your system. Follow this: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

I also recommend using xorg-edgers driver: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

---

### Post by avengerxp on 2010-10-01
thanks for the help n advice (i like to hear this kind of answers, instead of NOs)

am trying them out now. will keep you updated.

cheers!

---

### Post by avengerxp on 2010-10-02
Update : So far No go

i have followed the thread on hot to install the driver... followed upto downloading the latest package.

installed the security hot fix too.

when i try to create the deb package the terminal spits this error

> dharshan@MyLinuxBoX:~$ sh ati-driver-installer-10-9-x86.x86_64.run --buildpkg Ubuntu/lucid
Created directory fglrx-install.gA6FTs
Verifying archive integrity...Error in MD5 checksums: 900fa246e9246a4b59de6ba38344bc95 is different from 5affd3ef0454ef7d727c439466c2654c
dharshan@MyLinuxBoX:~$ sudo dpkg -i fglrx*.deb
[sudo] password for dharshan: 
dpkg: error processing fglrx*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx*.deb
dharshan@MyLinuxBoX:~$ 

Downloaded the same package twice to make sure it wasn't corrupt. get the same MD5 error.

any ideas.

---

### Post by Yellow Pasque on 2010-10-03
You are following the wrong section of the guide..

---

### Post by avengerxp on 2010-10-04
well, after reading your feedback, i just got the clear idea, you only asked me to install the edgers drivers,,,,:confused:

so i went ahead to uninstall all the stuff that ATI patch has written etc.

after restarting i found out that my Keyboard (PS2) and mouse(USB) not working in Gnome.

when i boot into terminal mode it works (recovery). but does not work anyway in GUI.

any help to fix this

---


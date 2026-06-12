---
title: "Help installing Jahkasha tar.gz"
date: 2008-11-11
forum: Multimedia Software
---

### Post by cocopuffz on 2008-11-11
I'm trying to install Jahshaka using the usual "./config && make" and variants of it that I've found online, but I can't get it to install.

Can someone please type the command to install this file? I'm not sure what switches I'm supposed to use. Can someone please type out exactly what I'm supposed to enter in the command line?

---

### Post by xc3RnbFO8P on 2008-11-11
Did you do:
extract the /home/your folder/Desktop/jahshaka.tar.gz
In Terminal:
cd /home/your folder/Desktop/jahshaka
./configure
make
sudo make install

---

### Post by cocopuffz on 2008-11-11
That's exaclty what I did. I'll try again when I get home. I may have inserted some switches that I read in the help/man files.

Thanks

---------EDIT---------

Still didn't work. This is what I get...
-----------------------------------------------------------------
./configure: 57: qmake: not found


SYNOPSIS

     ./configure [ switches ]
     ./configure [ switches ] jahshaka
     ./configure [ switches ] jahplayer

DESCRIPTION

     Configures the jahshaka build process to build either jahshaka
     or jahplayer

     By default running configure with no arguments will activate the
     build for jahshaka

     You need to follow the configure command with the make command
     in order to actually build the software!

SWITCHES

     --prefix=path
          sets the path for the installation (default: /usr/local)

     --disable-debug
          sets debug mode off

     --disable-plugins
          disables the plugin build and install

     --enable-static
          disables the dynamic loading of various open libraries
-----------------------------------------------------------------------------

I'm sure it's something simple I'm missing. Can anyone shine a light on what I'm missing. I'm assuming it's one of the switches.. or that I must be missing qt or qmake...

---

### Post by xc3RnbFO8P on 2008-11-12
Yes it should be **./configure**

EDIT:

You have to install Open Libraries.
> Ubuntu 8.04 does not ship the required version of CMake. Please install the intrepid version. (Available from archive.ubuntu.com ) 
Read this:
[http://www.openlibraries.org/wiki/BuildingUbuntuEight]("http://www.openlibraries.org/wiki/BuildingUbuntuEight")

---

### Post by cocopuffz on 2008-11-12
thanks for all the help. I'll give it another go on the machine it's intended to run on. I installed qt dev tools which allowed me to advance in the install process, but it failed at the point where I needed the openlibraries. That link you provided might be the solution. I'll know on friday when i get a chance to try.

Thanks!

---


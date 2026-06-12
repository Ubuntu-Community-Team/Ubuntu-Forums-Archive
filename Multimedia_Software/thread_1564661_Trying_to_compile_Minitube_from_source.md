---
title: "Trying to compile Minitube from source"
date: 2010-08-30
forum: Multimedia Software
---

### Post by JohnElway on 2010-08-30
I'm trying to install the latest version of Minitube on my 64 bit Ubuntu 10.04 installation. I thought adding a PPA would let me upgrade from version 0.9 to the latest version but it didn't seem to work. So now I'm trying to install from source (I've never done this before so I'm a complete noob when it comes to compiling). I checked the install instructions in the source which reads:

```
# Build instructions

## Prerequisites

To compile Minitube you need Qt >= 4.5 installed.

On a Debian or Ubuntu system just type:
    sudo apt-get install build-essential qt4-dev-tools libphonon-dev

Windows and Mac users can get the Qt libraries from:
http://qt.nokia.com/downloads

## Compiling

Compiling on Linux is fairly easy. Just run:
    qmake
and then
    make

Beware of the Qt3 version of qmake! If things go wrong try running qmake-qt4 instead.

## Running

Just type:
    ./build/target/minitube
```

Ok so I installed the prerequisite packages, but just to be safe I wanted to run the ./configure command, but when I try to I get the "bash: ./configure: No such file or directory" message. Any idea what I'm doing wrong? Also, based on what I've read, I should have to enter some kind of install command in order to install the compiled binary but the instructions make no mention of this. Am I missing something?

EDIT: Oops, I posted this in the wrong section. Can someone move this to General Help or wherever would be appropriate?

---

### Post by zpletan on 2010-08-30
1) There is no configure script to run (I checked).
2) To install, you might try running ```
make install
```  No idea how that will work though.

---

### Post by mc4man on 2010-08-30
For the source build (latest 1.1 - the 1.0 doesn't work here or anywhere

cd to source folder and run 
```
qmake && make
```
or on 1 install I needed to do (if qt3 headers, ect. are installed
```
qmake-qt4 && make
```

Then if you want 
sudo make install
or install checkinstall and use
```
sudo checkinstall --backup=no --deldesc=yes --delspec=yes --deldoc=yes --pkgname minitube --pkgversion 1.1  --default
```
 
1.1 source here if trying to build 1.0
[http://flavio.tordini.org/minitube#download](http://flavio.tordini.org/minitube#download)

---


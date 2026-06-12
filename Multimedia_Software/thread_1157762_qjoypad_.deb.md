---
title: "qjoypad .deb"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Siggma on 2009-05-13
I go to used to using my gamepad to run mplayer I felt lost and forlorn without a gamepad key mapper. So, I managed to make a qjoypad.deb file you are all welcome to fetch and try. The source is arranged incorrectly and I haven't taken the time to figure out how to fix it yet. The package is named incorrectly for a repo but I'll eventually get it updated. 
I'm not the maintainer. I just managed to compile it from the source at [http://qjoypad.sourceforge.net](http://qjoypad.sourceforge.net) into a deb package using the newer libqt3-mt library. It "should" correct the dependency issue. You will need to install the libqt3-mt manually and the package is named "src" so if you want to remove it, remove the package named "src", not qjoypad. 

Installation:
```
wget http://www.trbailey.org/files/qjoypad_20090512-1_i386.deb
sudo apt-get install libqt3-mt
sudo dpkg -i qjoypad_20090512-1_i386.deb
```

Create a new item under "System->Preferences->Startup Applications
Add a description like "Qjoypad"
Enter the following for the command. You can adjust the sleep time up or down depending on your system start speed 
```
sh -c "sleep 10 && /usr/local/bin/qjoypad"
```
or remove it completely.
```
sh -c "/usr/local/bin/qjoypad"
```

Logout and Login again and you should see the icon in the task area.

Feedback?
Do the Icons work?

I promise I'll fix up a copy eventually.

---

### Post by Siggma on 2009-05-13
You can probably ignore this. I probably won't work. 

Note that there is a compiled binary already in the src/ directory of the qjoypad archive. I haven't gotten the icons to work yet but the binary is fine.

Sorry :(

---

### Post by RegressLess on 2009-09-22
Let me be the first to say thanks. With some help, I installed qjoypad 4.0, but had problems. 3.4 works a lot better and is easy to install, thanks to you!

---

### Post by jukingeo on 2009-10-14
> **Siggma said:**
> You can probably ignore this. I probably won't work. 

Note that there is a compiled binary already in the src/ directory of the qjoypad archive. I haven't gotten the icons to work yet but the binary is fine.

Sorry :(

Does the install for qjoypad work?  I followed the directions for the current version that is uploaded to sourceforge however, the installation (as described in the "install" instructions) isn't working.

Here is my terminal output:

geo@home:~/qjoypad-4.0.0/src$ ./config
_./config: line 66: qmake: command not found_

Configuring QJoyPad installation...
------------------------------------------------------------

Device directory: /dev/input
-- Devices will be looked for in:
     /dev/input/js0
     /dev/input/js1
     etc.

Prefix directory: /usr/local
-- Files to be installed in:
     /usr/local/bin
     /usr/local/doc
     /usr/local/share/pixmaps
	 
---------------------------------------------------------
If these settings are okay, go ahead and run 'make' and
then 'make install'.

To make changes, run ./config --help for details.

geo@home:~/qjoypad-4.0.0/src$ make
make: *** No targets specified and no makefile found.  Stop.
geo@home:~/qjoypad-4.0.0/src$ 

I underlined what I think is the problem.   Any assistance in getting this running would be appreciated.  I need the program for a Halloween event I am putting together and I need joystick support for a program that right now only operates from the keyboard.

Thanx,

Geo

---

### Post by tylerious on 2009-10-24
I got the same qmake error when I ran ./config. It means you do not have the QT development packages installed. "sudo apt-get install qt4-dev-tools" should get you the necessary packages in Jaunty.

You also might not have the c++ compiler installed - at least, I didn't. Mind that Jaunty calls the executable /usr/bin/g++-4.3 or something instead of /usr/bin/g++, so I made a symbolic link so the makefile would work.

I hope this helps some. I'm trying to compile it too and learning as I go, so that's all I have figured out right now.

EDIT:
You should make sure you have the packages "g++-4.3" and "libxtst-dev" installed. I was able to successfully build qjoypad - good luck, jukingeo!

---


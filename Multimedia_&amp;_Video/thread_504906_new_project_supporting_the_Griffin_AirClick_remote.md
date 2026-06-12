---
title: "new project supporting the Griffin AirClick remote control"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by bryan.taylor on 2007-07-19
Note: If you need support, then either post in this thread or send me an email at [email]bryan.a.taylor@gmail.com[/email].  Do not send me a pm.  I check that email regularly.

The first public release of the airclick project ([http://sourceforge.net/projects/airclick](http://sourceforge.net/projects/airclick)) is now available on sourceforge.  It provides for complete customization of the Griffin AirClick remote control ([http://www.griffintechnology.com/products/airclickusb/](http://www.griffintechnology.com/products/airclickusb/)).

I saw that some people (myself included) were having issues getting the airclick-mngr software to work, so I wrote a replacement.  I had tried to make airclick-mngr work, but I had issues with the applet.  It didn't remain in the system tray, it wasn't very configurable, and after looking at the code I found that there were usability issues.

This new airclick project allows for complete customization of your remote based on which application is currently active.  It supports button repetition (holding down a button), double clicking a button, and supports pressing different combinations of buttons.  In total, it supports 62 different button actions per application, although using more than ~30 might be a bit of a hassle due to the layout of the buttons on the remote.

My brother and I have been using this for the past couple of weeks, and most of the bugs have been worked out.  I hope that someone else finds this to be as useful as we do.

---

### Post by sastian on 2008-01-30
after recieving my airclick (which im plannin on using with Elisa)
ive run into a roadblock...

a little history..
IM running a 7.10 install completely upgraded.
Useing Elisa primarily for a media center

-downloaded the airclick manager...
-changed permissions as stated in the readme..
-ran ./configure
-got an error about no compiler being installled
-i installed g++
- ran ./configure again 
.. this time got a bit further but it stops at this step...

[B]checking for XStringToKeysym in -lX11... no
X11 library not found![/B]

any help would be appreciated....

heres a terminal dump
```
sastian@Media-Center:~/Desktop/airclick/airclick-0.6.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for XStringToKeysym in -lX11... no
X11 library not found!
sastian@Media-Center:~/Desktop/airclick/airclick-0.6.2$ ./configure help
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for help-g++... no
checking for help-c++... no
checking for help-gpp... no
checking for help-aCC... no
checking for help-CC... no
checking for help-cxx... no
checking for help-cc++... no
checking for help-cl.exe... no
checking for help-FCC... no
checking for help-KCC... no
checking for help-RCC... no
checking for help-xlC_r... no
checking for help-xlC... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for help-gcc... no
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for XStringToKeysym in -lX11... no
X11 library not found!
sastian@Media-Center:~/Desktop/airclick/airclick-0.6.2$ make
make: *** No targets specified and no makefile found.  Stop.
sastian@Media-Center:~/Desktop/airclick/airclick-0.6.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for XStringToKeysym in -lX11... no
X11 library not found!
sastian@Media-Center:~/Desktop/airclick/airclick-0.6.2$ 
```

---

### Post by bryan.taylor on 2008-01-30
My linux box has died since I wrote this application, so I can't easily verify what I'm about to tell you.

You are missing the **xorg development libraries**.  Google tells me that a likely location for these libraries is the xorg-dev package (this is probably the one) or the x11-dev package (superseded by xorg-dev?).

---

### Post by briactex on 2008-01-31
This is great that someone is working on it...I am quite new here....in case you could help me, I am running Gutsy Gibbon, i successfully ran the ./configure, but when i ran the make it gives me :

root@briac-laptop:/home/briac/Documents/airclick-0.6.2# make
make  all-recursive
make[1]: Entering directory `/home/briac/Documents/airclick-0.6.2'
Making all in src
make[2]: Entering directory `/home/briac/Documents/airclick-0.6.2/src'
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
mv -f .deps/main.Tpo .deps/main.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT config.o -MD -MP -MF .deps/config.Tpo -c -o config.o config.cpp
mv -f .deps/config.Tpo .deps/config.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT device.o -MD -MP -MF .deps/device.Tpo -c -o device.o device.cpp
mv -f .deps/device.Tpo .deps/device.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT keygen.o -MD -MP -MF .deps/keygen.Tpo -c -o keygen.o keygen.cpp
mv -f .deps/keygen.Tpo .deps/keygen.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT util.o -MD -MP -MF .deps/util.Tpo -c -o util.o util.cpp
mv -f .deps/util.Tpo .deps/util.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT ac_exception.o -MD -MP -MF .deps/ac_exception.Tpo -c -o ac_exception.o ac_exception.cpp
mv -f .deps/ac_exception.Tpo .deps/ac_exception.Po
g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT platform.o -MD -MP -MF .deps/platform.Tpo -c -o platform.o platform.cpp
mv -f .deps/platform.Tpo .deps/platform.Po
g++  -g -O2   -o airclick main.o config.o device.o keygen.o util.o ac_exception.o platform.o  -lXtst -lX11 
make[2]: Leaving directory `/home/briac/Documents/airclick-0.6.2/src'
make[2]: Entering directory `/home/briac/Documents/airclick-0.6.2'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/briac/Documents/airclick-0.6.2'
make[1]: Leaving directory `/home/briac/Documents/airclick-0.6.2'
root@briac-laptop:/home/briac/Documents/airclick-0.6.2# make install
Making install in src
make[1]: Entering directory `/home/briac/Documents/airclick-0.6.2/src'
make[2]: Entering directory `/home/briac/Documents/airclick-0.6.2/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'airclick' '/usr/local/bin/airclick'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/briac/Documents/airclick-0.6.2/src'
make[1]: Leaving directory `/home/briac/Documents/airclick-0.6.2/src'
make[1]: Entering directory `/home/briac/Documents/airclick-0.6.2'
make[2]: Entering directory `/home/briac/Documents/airclick-0.6.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/briac/Documents/airclick-0.6.2'
make[1]: Leaving directory `/home/briac/Documents/airclick-0.6.2'
root@briac-laptop:/home/briac/Documents/airclick-0.6.2# airclick
Thu Jan 31 21:38:48 2008|Info : Initializing...
Thu Jan 31 21:38:48 2008|Info : Logging to (/root/.airclick/airclick.log)
Thu Jan 31 21:38:48 2008|Info : Logging to Console
Thu Jan 31 21:38:48 2008|Error: Unable to query DISPLAY environment variable!
Thu Jan 31 21:38:48 2008|Error: aborting...

Do you have any idea?
my remote is the last think I cannot use on Ubuntu...it would be so nice to make it work

thanks
bri

---

### Post by briactex on 2008-01-31
i had the same error as you sastian, i just instaledl libx11-dev, and after it will ask for libxtst-dev.
tell me if you your "make" command works for you

---

### Post by bryan.taylor on 2008-02-01
briactex, your DISPLAY environment variable isn't set while running as root.  Try running airclick under your normal user account.  It shouldn't need root privileges to run.
I seem to recall that you *might* have to change the permissions on your airclick remote device file.  The changes can be made permanent by creating a rule in your udev config files.

The first time you run airclick, you should probably run it with the following command line to make sure that everything is working properly:
```
airclick -l d
```

You may get an error message that looks something like this:
```
Fri Feb  1 13:36:36 2008|Debug: /dev/hiddev0: No such file or directory
Fri Feb  1 13:36:36 2008|Debug: errno = ENOENT
```

This means that you need to specify the correct device file for your airclick remote in the airclick.conf file.

---

### Post by ckgreenman on 2008-03-08
I have a quick question.   Is it possible to define a "global" action to a specific button action?    For example, I'd like to configure airclick to advance to the next virtual desktop (normally Control_L+Alt_L+Right) to say a double click on the "Next" button.  Failing in that would it be possible to assign Button actions to say the window manager or the desktop pager?


Thanks

---

### Post by bryan.taylor on 2008-03-09
If you look in the airclick.conf.sample file included in the tarball, you will see a section like this at the bottom:

```
# most of these defaults control my amarok music player
BeginSection
	Application	default
	# play/pause (amarok)
	BeginMacro
		Button "Play/Pause"
		BeginCombination
			Super_L
			Home
		EndCombination
	EndMacro
	# seek backward (amarok)
	BeginMacro
		Button "Previous"
		BeginCombination
			Super_L
			Shift_L
			KP_Subtract
		EndCombination
	EndMacro
.
.
.
	# switch to workspace left
	BeginMacro
		Button "VolumeDown"
		Button "Previous"
		BeginCombination
			Control_L
			Alt_L
			Left
		EndCombination
	EndMacro
	# switch to workspace right
	BeginMacro
		Button "VolumeUp"
		Button "Next"
		BeginCombination
			Control_L
			Alt_L
			Right
		EndCombination
	EndMacro
EndSection
```

That is how you add default actions to the buttons.  Any application specific customizations (like the ones above the default section in airclick.conf.sample) will take precedence over the default actions.

---

### Post by ckgreenman on 2008-03-09
Oh DUH!!!.     I guess it helps to read the ENTIRE config file, LOL.   


Thanks for the response.    Awesome app, btw.   

Now I need to write a snazzy script for udev to run that will fire up airclick as the correct user when I plug it in :)

---

### Post by bryan.taylor on 2008-03-25
I"ve added a minor release to fix a bug that my brother ran into.  The new version is 0.6.3.

Also, someone suggested to me that I should consider adding CD player style button functionality to airclick.  This means that there would be three types of actions:
1) Single Click
2) Double Click
**3) Hold down the button for, say, 1 second**

Each of these actions would be repeatable.  If there is enough interest then I may add this, but I wanted to see what everyone else thought about it.

---


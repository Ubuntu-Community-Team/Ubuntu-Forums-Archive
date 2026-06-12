---
title: "lcdproc lis drive issue"
date: 2010-03-10
forum: Mythbuntu
---

### Post by sfuse on 2010-03-10
I've been trying to install the lis driver for lcdproc with no luck.  The configure script says it needs the ftdi library installed, which I do, as well as the libftdi-dev package.  I have seen where there have been some issues in the past with this driver but I have yet to find a solution that works for me.  The most recent solution I have found was here:

[https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/178599](https://bugs.launchpad.net/ubuntu/+source/lcdproc/+bug/178599)

I don't understand why the lcdproc configure script can't see the ftdi library it needs.  Any suggestions would be appreciated.

---

### Post by bgiannes on 2010-05-05
under 9.10 this script works.

but after upgrading to 10.04 the script runs and builds lcdproc but i can't get the display to work....

the lcdproc 0.5.3 package is said to have the L.I.S driver but it wouldn't work for we....

---

### Post by bgiannes on 2010-05-07
well both the "cvs script file install" and the repo and compiling from source will not make the lis.so file, it's broken.

./configure --enable-libusb --enable-drivers=lis (it saids ftdi is needed, but it is installed, it doesn't list anything in the drivers to be install list)
so make, sudo make install doesn't do anything.



so to get it working, (ugly hack) i install lcdproc on a 9.10 PC then copyed the lis.so file to the 10.04 PC into the /usr/lib/lcdproc/ dir.  setup the LCDd.conf and it works, (but only uses half the LCD display?)

---

### Post by sireone on 2010-11-01
Did you ever find a solution to this?  Having the exact issue on XBMC with lis driver.

---

### Post by bgiannes on 2010-11-17
have a look at this...

[http://forum.xbmc.org/showthread.php?t=79433](http://forum.xbmc.org/showthread.php?t=79433)



:~$ sudo apt-get install libftdi1 libftdipp-dev libftdi-dev libftdipp1
:~$ sudo apt-get build-dep lcdproc  

You will have to download the Source code and compile (makes the lis.so file):

~$ wget [http://softlayer.dl.sourceforge.net/project/lcdproc/lcdproc/0.5.3/lcdproc-0.5.3.tar.gz](http://softlayer.dl.sourceforge.net/project/lcdproc/lcdproc/0.5.3/lcdproc-0.5.3.tar.gz)
~$ tar xvfz lcdproc-0.5.3.tar.gz
~$ cd lcdproc-0.5.3
~$ ./configure --enable-drivers=all
~$ make
~$ cd shared
~$ make
~$ cd ../server
~$ make
~$ sudo make install
~$ cd ../clients
~$ make
~$ sudo make install
~$ mkdir lcd
~$ cp lcdproc-0.5.3/server/drivers/lis.so lcd/lis.so 

But, then i copyed the lis.so file to the default loction, (as i already have a working config file)

~$ cp lcd/lis.so /usr/lib/lcdproc 

Changed the file user and group to root, then restart LCDproc

UPDATE:
This works......
the L.I.S. works with full display...

I recommend doing a sudo apt-get install lcdproc 1st and just use the stock install with the lis.so file in place.

---

### Post by sireone on 2010-11-19
I've tried both apt-get and source version.  Still only shows on the left half of the display.  This issue actually started with 10.04.  Worked fine with 9.11.

---

### Post by bgiannes on 2010-11-22
> **sireone said:**
> I've tried both apt-get and source version.  Still only shows on the left half of the display.  This issue actually started with 10.04.  Worked fine with 9.11.


not sure why i have the full display now...

did you;
sudo apt-get install libftdi1 libftdipp-dev libftdi-dev libftdipp1

then a
sudo apt-get install -f

then build the lis.so file...

---

### Post by sireone on 2010-11-22
Yep..did that.  But for some reason apt-get is not installing lcdproc correctly. I noticed that no init scripts files were created.  This is what I get when I run apt-get install -f lcdproc:

```
xbmc@XBMCLive:~$ sudo apt-get install -f lcdproc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lcdproc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/378kB of archives.
After this operation, 1,270kB of additional disk space will be used.
Selecting previously deselected package lcdproc.
(Reading database ... 63614 files and directories currently installed.)
Unpacking lcdproc (from .../lcdproc_0.5.3-0ubuntu2_i386.deb) ...
Processing triggers for ureadahead ...
Setting up lcdproc (0.5.3-0ubuntu2) ...
```

---

### Post by paulpoco on 2010-11-28
I got it to work following my instructions but cannot get the xbmc lcd info to take priority over the lcdproc server info.  XBMC Dharma doesn't have the enable LCD/VFD option on RC1, but changing the guisettings.xml haslcd to true enabled the XBMC info.  Maybe the XBMC devs took other lcd stuff out on RC1 other than the settings enable?

---


---
title: "update kernel to 24 and my nvidia card remove"
date: 2009-09-14
forum: Multimedia Software
---

### Post by eAi-T0ky0 on 2009-09-14
hi

  I have update my kernel for 24 and the nvidia driver remove , I use ubuntu 8.04 and my nvidia card is Geforce 6200 

I don't know how to install my driver nvidia , I install the driver from web page of nvidia it come .run  , I try to install it from terminal but it give me error that can't find a file and can't meta , i don't know what meta mean? :(


So if i can restore my old kernel I have a back up from it , I JUST NEED TO GET MY SCREEN DRIVER BACK :confused:

---

### Post by eAi-T0ky0 on 2009-09-14
Bump????

---

### Post by HappyFeet on 2009-09-14
Go to system>administration>hardware drivers

---

### Post by eAi-T0ky0 on 2009-09-15
I have go to system>administration>hardware drivers 

and there NOTHING

I want to tell you , that i found the driver there when i install ubuntu at first time i install it and it work , but when I update the kernel the driver go from system>administration>hardware drivers , and the screen go bigger that usual.

I have read some tips in "Kernel and Mesa Updates" from ubuntu help wiki

[https://help.ubuntu.com/community/NvidiaManual#kernelandmesa](https://help.ubuntu.com/community/NvidiaManual#kernelandmesa)

I have download the driver from the web of nvidia

```
NVIDIA-Linux-x86-185.18.36-pkg1.run
```

and put it in home

and in terminal

```
bac@Linux:~$ sudo sh NVIDIA-Linux-x86-185.18.36-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 185.18.36........................................................................................................................................................................................................................................................................................................
```

it give me error

[IMG]http://img199.imageshack.us/img199/1896/screenshotvy.jpg[/IMG]

[http://img199.imageshack.us/img199/1896/screenshotvy.jpg](http://img199.imageshack.us/img199/1896/screenshotvy.jpg)

the nvidia log file at "/var/log/nvidia-installer.log"

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Sep 29 20:54:35 2007
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '6043'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       www.nvidia.com.
```

I don't know what i can do? :confused::confused::confused::confused::confused:

---

### Post by eAi-T0ky0 on 2009-09-15
OK , now i have remove my new kernel 24 and now i'm use 23 my old kernel and the problem of nvidia still there , please some one told me any thing. :(:(:(:(

---

### Post by eAi-T0ky0 on 2009-09-15
nobody know thing for god save I have 2 days no one help

---

### Post by ivanhelguera on 2009-09-16
Just a note to let you know that I face a similar problem. 
No solutions yet, but I'll let you know of any progress.

---

### Post by ivanhelguera on 2009-09-17
hello, 
i had a similarr problem, as I wrote, and in the end I finished reinstalling the system. I had a separate /home patrtion, so i was more or less painless. 
I have two ideas: 
1) update to 8.1, and then possibly 9.04. The whole system should be reinstalled, and that *might* - or not - help. 
2) use envy. Install envy (sudo apt-get envyng-gtk)  first, then try dealing with nvidia drivers through the application. 

My suggestion would be to try to uninstall the drivers you ried to install through the script with envyng, and then doing a distribution upgrade. You may try to see what happens if you try to install nvidia drivers through envyng - maybe that would work.
I am not an expert in the field, so those are just suggestions on my part. 
Don't give up! 
Cheers, 
IH

---

### Post by ivanhelguera on 2009-09-17
Sorry! I'm ill, and that's why I misunderstood your situation. 
So, all in all, from the error you got I see that you DID NOT do the manual install of nvidia? The script reported the error and closed, I assume. 
That is because you ran it in graphic mode - you fired you terminal window in XFCE (as I assume) and tried to launch it from there. This is NOT the way to go: in order to run the script you have switch to the pure text environement (ALT+F1), close the graphical system by command such as 
```
sudo /etc/init.d/gdm stop
```
(maybe its xdm instead of gdm in XFCE?). Then you can start the script, and after it completes, you restart the gdm 
```
sudo /etc/init.d/gdm start 
```
after which you go back to the graphic environement with ALT-F7. 
From what you write it seems to me that it might be a bit to complicated for you. (I am no linux expert, mind you!). I am by no means sure that this is the whole way to go; actually you should probably take some additional steps from the command line, possibly removing some startup scripts in /etc/init.d/. 
As I said, I have an impression that this way might be bit to complicated. If you don't know about ttys, startup scripts, you'd be fighting in the dark, and small mistakes might make things difficult. 
As much as I am willing to help, I do not know enough about that system to guide you more precisely. 
BUT: 
As I said in the previous post, the envy road is open to you. I'd seriously try using envyng, and updating to 8.10 and possibly 9.04 after that. 
If you have any question, I;ll be following the thread. My knowledge is limited, but miht be useful. 
Take care that I live in Warsaw, Poland, so our time zones are quite different. 
Good luck, 
IH

---

### Post by eAi-T0ky0 on 2009-09-17
> **ivanhelguera said:**
> BTW: what happens when you boot to the old kernel in Grub?
EDIT: sorry, I see that you already tried that.

[COLOR="Red"]Yes i tried that before and it give me a black screen or some installing doing it and at the end he say put the password of root or login I put it he say it incorrent , I do "Esc" and it do nothing it log in system with the same problem and nvidia driver not there in hardware!!![/COLOR]

EDIT 2: 
Sorry! I'm ill, and that's why I misunderstood your situation. 
So, all in all, from the error you got I see that you DID NOT do the manual install of nvidia? The script reported the error and closed, I assume. 
That is because you ran it in graphic mode - you fired you terminal window in XFCE (as I assume) and tried to launch it from there. This is NOT the way to go: in order to run the script you have switch to the pure text environement (ALT+F1), close the graphical system by command such as 
```
sudo /etc/init.d/gdm stop
```
(maybe its xdm instead of gdm in XFCE?). Then you can start the script, and after it completes, you restart the gdm 
CODE]sudo /etc/init.d/gdm start [/CODE]
after which you go back to the graphic environement with ALT-F7. 
From what you write it seems to me that it might be a bit to complicated for you. (I am no linux expert, mind you!). I am by no means sure that this is the whole way to go; actually you should probably take some additional steps from the command line, possibly removing some startup scripts in /etc/init.d/. 
As I said, I have an impression that this way might be bit to complicated. If you don't know about ttys, startup scripts, you'd be fighting in the dark, and small mistakes might make things difficult. 
As much as I am willing to help, I do not know enough about that system to guide you more precisely. 

[COLOR="Red"]OK i tried that too , and do the script ok and it not work too , the same problem is there I exit from x server and I have install nvidia manual but the same problem is there , in me I don't think that good to install nvidia manual but i have try it.[/COLOR]

BUT: 
As I said in the previous post, the envy road is open to you. I'd seriously try using envyng, and updating to 8.10 and possibly 9.04 after that. 
If you have any question, I;ll be following the thread. My knowledge is limited, but miht be useful. 
Take care that I live in Warsaw, Poland, so our time zones are quite different. 
Good luck,
IH

[COLOR="Red"]
I do install envy now and I see that COPMIZ work , and the all things of nvidia works now when I install nvidia from envy

The x server setting work too , but the nvidia not in hardware. i don't know how x server settings work and the drive not there.

The problem now is in screen resolution , The max resolution found in x server setting and screen resolution NOW is 640*480 :(

see that out put maybe you need:

```
bac@Linux:~$ modprobe -r nvidia
FATAL: Module nvidia is in use.
```

```
bac@Linux:~$ cat /proc/version
Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 21:47:28 UTC 2009
```

I'm pretty sure that drive install , but not sure about resolution is to big in screen see the picture you can see the x server setting of nvidia and the it work great but as you see the x server setting take a whole screen I can't found the X button 
[IMG]http://img338.imageshack.us/img338/5198/screenshoti.jpg[/IMG]
[http://img338.imageshack.us/img338/5198/screenshoti.jpg](http://img338.imageshack.us/img338/5198/screenshoti.jpg)
[/COLOR]



Now drive work after install it by Envy , thank all , but the resolution is too low,

---

### Post by ivanhelguera on 2009-09-17
> **eAi-T0ky0 said:**
> Now drive work after install it by Envy , thank all , but the resolution is too low,

OK. 
I undsersatnd you do not see the nvidia card in hardware drivers. That seems to me not very toublesome, as the envy is an *alternative* way of dealing with hardware drivers. Actually I've never used it, and I do not know much as to how 'Hardware Drivers" work, but that's the impression I got from what I read.
Anyhow, your problem now is that you only get a 640*400 screen resolution, right?
The important thing is that you have the driver working. 
Going for ```
modprobe -r nvidia 
``` is not a good idea, as it attempts to remove the driver, and - thanks god! - just gave the error message that the driver is in use. 
It seems, thouh, that the file /etc/X11/xorg.conf is misconfigured. It's there that the available screen resolutions are defined. Could you please paste the content of the file? (you can open it by gedit or any text editor, and then paste it here). 
In the screen you pasted there seems to be an option to change the resolution (the 640x480 box). Does anything happens when you do click on the box and then click apply?

---

### Post by eAi-T0ky0 on 2009-09-17
> **ivanhelguera said:**
> OK. 
I undsersatnd you do not see the nvidia card in hardware drivers. That seems to me not very toublesome, as the envy is an *alternative* way of dealing with hardware drivers. Actually I've never used it, and I do not know much as to how 'Hardware Drivers" work, but that's the impression I got from what I read.
Anyhow, your problem now is that you only get a 640*400 screen resolution, right?
The important thing is that you have the driver working. 
Going for ```
modprobe -r nvidia 
``` is not a good idea, as it attempts to remove the driver, and - thanks god! - just gave the error message that the driver is in use. 
It seems, thouh, that the file /etc/X11/xorg.conf is misconfigured. It's there that the available screen resolutions are defined. Could you please paste the content of the file? (you can open it by gedit or any text editor, and then paste it here). 
In the screen you pasted there seems to be an option to change the resolution (the 640x480 box). Does anything happens when you do click on the box and then click apply?

[COLOR="Red"]thank you for the quick replay , I think the problem is in this file too bec the compiz work and all command i do for make sure the nvidia is install is good and it say it in use and X SERVER work as you see it in the picutre at last replay I do , The out put of my xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
EndSection


```[/COLOR]

I hope the solution there , I have 4 days now search for help :(

---

### Post by eAi-T0ky0 on 2009-09-17
I just try to change screen from command line

gksu displayconfig-gtk

and it tell me an error

all user must log off for the changes to take effect

---

### Post by eAi-T0ky0 on 2009-09-17
the problem have been solved :)


The Solution :

The time zone was not corrent when I make it corrent and restart the screen come back with my normal resolution , the compiz work , all thing going good :P

thank you all

thank you ivanhelguera for try to helping me i like u :P

---

### Post by ivanhelguera on 2009-09-18
my pleasure - have fun with your box

---


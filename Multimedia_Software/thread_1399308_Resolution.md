---
title: "Resolution"
date: 2010-02-05
forum: Multimedia Software
---

### Post by jimmers on 2010-02-05
Hi All,
Here we go again, since Gutsy Ubuntu 7-10, Ihave been dual booting with XP on my Desk Top with no problems,both OS's displayed at 1024x768 which was good through to Jaunty when someone whom I allowed to check their emails, must have done something!!!!, outcome is I have a resolution of 800x600, in Jaunty.
I think it is a problem with Ubuntu, I have tried Karmic, Mint 8 and a release of Lucid and they all display 800x600 on the other hand  I have tried OpenSuse 11 and Puppy and they both display in 1024x780, I have tried xrandr, with no joy, and Admin hardware Drivers and all I get is "No Proprietary Drivers are in use on System".
It is because of this that I had buy a Lap-top dedicated as a Ubuntu Machine, for personal use, but as I Work from home, often, but not always I need a dual booting machine, I do not want to put Windoze on the Lap-top, as this is the machine that I try to convert the great un-washed.

I don't always have the Lap-top at home, as said  that is why I need my resolution back.

Sorry about the long pre-amble.

All help, Suggestions, Ideas, as always greatly appreciated

---

### Post by Cabs21 on 2010-02-05
you need to be connected to the internet for the Drivers to Update properly.  What type of video card are you using?

---

### Post by lidex on 2010-02-05
What is the output of this command in a terminal (Applications>Accessories>Terminal):
```
lspci -nn | grep VGA
```

---

### Post by jimmers on 2010-02-06
lidex, Cabs21 Hi,
As requested here is the information
The output is :-
  	 	 	 	 	 	  ubuntu@ubuntu:~$ sudo lspci -nn | grep VGA  
 01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] [1106:3108] (rev 01) 



I think it is outdated and needs new driver.

---

### Post by lidex on 2010-02-06
Support for older video cards is frequently dropped in newer driver versions so not always a good idea to use the latest with them. First try using the vesa driver as this fellow did:
[http://ubuntuforums.org/showthread.php?t=1340466]("http://ubuntuforums.org/showthread.php?t=1340466")
[I know his problem was different-don't worry about that] You don't want to "copy" that xorg, just specify the vesa driver. To edit enter this command:
```
gksudo gedit /etc/X11/xorg.conf
```

Logically I would think that you should be able to ascertain the driver in the working configurations and apply here if vesa doesn't work.

---

### Post by jimmers on 2010-02-07
Guys,
I thank you for all your help and advice, but I think the problem is now solved!!!!!!
my desktop hard-drive has finally given up the ghost, I can no longer open WINDOZE or Ubuntu.

Again I thank you for all Help

---


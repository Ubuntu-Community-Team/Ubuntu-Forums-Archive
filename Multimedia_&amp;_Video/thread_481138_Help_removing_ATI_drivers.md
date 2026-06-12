---
title: "Help removing ATI drivers"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by Redbomber on 2007-06-22
I have mucked around with my video drivers (ATI x800) and now I'm having issues.  What I did was installed the driver from the ATI web site without removing the proprietary driver first.  Now, games won't run and Google Earth won't either.  

When I enable ATI accelerated graphics driver in restricted driver, I have to configure X-server after reboot, then after that the accelerated graphics driver is still not selected.  This didn't happen before.   

Can someone please help me completely remove all traces of these and install the proprietary driver again using the CLI?  I have finally got Ubuntu working the way I want it and really don't want to completely re-install for a 4th time.

---

### Post by sparkguitar05 on 2008-06-03
*bump*

I am in this EXACT same situation and desperately need help.

---

### Post by Kronie on 2008-06-15
BUMP
+1 same situation here(video x600), need help!

---

### Post by Kronie on 2008-06-15
U GUYS! Seriously! i fixed it!!!
ok so what i did was.
1) in synaptic, remove xserver-video-ati and xorg-driver-fglrx(this is the one that shows up in hardware manager)
2) restart
3) when you boot back in, everything will look crappy, you go to system->admin->hardware drivers, and u put a check on "use driver"(or sumthing) . it will install a fresh copy of fglrx.
4) restart(it will ask u to..)
5) enable the driver(system->hardware drivers->enable)
6) restart
7) login. if you will have issues with seeing ur desktop, restart xserver(ctrl+alt+backspace)
8) in the login screen press on options button(depends on what theme u have..but it should be in the bottom left corner), click on sessions and load FAILSAFE gnome, then enter ur nick/pass.
9) go to terminal and type
```
sudo gedit /etc/X11/xorg.conf
```
10) in the text file, look for "Driver "****"" in device section(the first section)
11) change whatever you have after driver to "Driver "fglrx" ", save.
12)in terminal type ```
sudo aticonfig --initial -f
```
13) restart
14) login as u usually would, and enjoy the show :P  

PS: to check if driver is in its place and up and running, after restart go to terminal and type "fglrxinfo" if it will output you with somethink like this:
```
kron@kron-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.7412 Release
```
then you are ready to rock.. if instead of ATI Tech. Inc. it will give you Mesa, reffer to this manual
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)

PPS: Steps 9-14 were taken from this manual [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Installation](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Installation)

---


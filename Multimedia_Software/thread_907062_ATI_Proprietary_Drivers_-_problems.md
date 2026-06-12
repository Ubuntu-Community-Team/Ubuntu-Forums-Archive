---
title: "ATI Proprietary Drivers - problems"
date: 2008-09-01
forum: Multimedia Software
---

### Post by scowcron on 2008-09-01
Here's the situation:

 I'm trying to get the game Anarchy Online to run through Cedega. When the game tries to load, after login I get to a solid black screen with game sounds running in the background. I read somewhere that somebody installed the proprietary drivers for their video card and it fixed this problem, so I thought I'd give it a shot but everything I've tried so far has failed. 

Here are some specifics:
Ubuntu Version: Ubuntu 8.04 Hardy Heron
~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

I've tried various methods including the ones found here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Using the menu in System>Administration>Hardware Drivers (this menu is completely blank, despite my having installed the proprietary drivers listed in the ubuntu repositories)

When I try and install ATI's linux drivers that I downloaded (ati-driver-installer-8.28.8.run) I get this message:

:~/Desktop$ ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...........................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

Any help or ideas would be much appreciated, thanks in advance.

---

### Post by scowcron on 2008-09-11
Still nothing. Allow me to simplify:

I'm trying to install the drivers for my ATI video card, listed above.
My "Hardware Drivers" menu is absolutely empty, it says no proprietary drivers are in use.

I've tried these methods as well as a couple of others:
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

When all is said and done, I still get this
####@#####:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

and my hardware drivers is still empty. Any ideas?

---

### Post by soxs on 2008-09-11
I would suggest you to purge all your ati restricted drivers.
The drivers which support your card suck, they really do.
Since the time, your card was bleeding edge, some years have passed and so the opensource support for you card has evolved.
You may try to set the driver (in your xorg.conf /etc/X11/xorg.conf, editable with sudo) to "radeon" or "ati" (I am not shure about that) and give that a shot.
GL btw.

---

### Post by scowcron on 2008-09-11
I've tried everything I did previously again, as well as purging and reinstalling all the drivers, editing xorg.conf various different ways, using the autoconfig again.

Still no direct rendering, still using the Mesa drivers.

When I boot up I get a dialog that reads as follows:

**Ubuntu is running in low-graphics mode**
Your screen and graphics card could not be detected
correctly. To use higher resolutions, visual effects, or multiple
screens, you have to configure the display yourself.

tried configuring it myself and none of it takes, just seems to default back to the mesa drivers.

---

### Post by soxs on 2008-09-12
As far as I know, radeon/ati are _PART_ of the meas stuff. So you don't need to wonder when setting "radeon" or "ati" as driver, when glxinfo spits mesa at you. It's just okay. You may try to run your game via wine anyways.

When you get that nasty "malconfigured x", I guess you messed around with fglrx, didn't you?

---

### Post by scowcron on 2008-09-13
Well to be honest i don't care whether it's the proprietary drivers or the mesa drivers running the video card, I believe the problem is that I cannot get direct rendering working that is giving me trouble.

The game actually runs now, I've tried wine and cedega both, and in both cases the game runs, but it uses 100% of my cpu and I get about 1 frame every 6-8 seconds. I know my computer can handle it because this computer used to have win XP on it and it ran just fine with that, and I've heard reports of it working from other people, as well as the game being on the games database for cedega.

As far as messing with the drivers to make direct rendering to work, I've tried everything I've found so far and nothing seems to work. I'm new to Ubuntu, have been running it for about 2 months now, and I just don't know what else to try.

---

### Post by soxs on 2008-09-13
> **scowcron said:**
> Well to be honest i don't care whether it's the proprietary drivers or the mesa drivers running the video card, I believe the problem is that I cannot get direct rendering working that is giving me trouble.

The game actually runs now, I've tried wine and cedega both, and in both cases the game runs, but it uses 100% of my cpu and I get about 1 frame every 6-8 seconds. I know my computer can handle it because this computer used to have win XP on it and it ran just fine with that, and I've heard reports of it working from other people, as well as the game being on the games database for cedega.

As far as messing with the drivers to make direct rendering to work, I've tried everything I've found so far and nothing seems to work. I'm new to Ubuntu, have been running it for about 2 months now, and I just don't know what else to try.
I woul like to help you, but my knowledge to such old cards is limited. I am sorry.
You may add some keywords to your thread (goto bottom): radeon, ati, 9000,

---


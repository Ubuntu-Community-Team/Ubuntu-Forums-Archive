---
title: "[SOLVED] Display problem in Ubuntu in ATi"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Canis familiaris on 2008-06-18
I use Ubuntu 8.04 Hardy AMD64. To start with it did not detect the correct resolution on install (chose a widescreen resolution for my CRT) and I had to correct it. But however the login screen still runs in that resolution and I wonder how to change it because many times on startup the monitor picture flickers and I have to restart X.

However my main question is that I have installed ATi through the repos, through Envy and also by downloading drivers from AMD but in each case on login no picture appears and all I get is a blank screen but I can hear the sound? What is the problem? 

Also in earlier version of Ubuntu I could select vesa as my driver by:
sudo dpkg-reconfigure xserver-xorg but now it does not give the option to choose the driver?

Help would be highly appreciated.

---

### Post by Canis familiaris on 2008-06-19
bump
help! anyone?

---

### Post by pietjanjaap on 2008-06-19
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).



logon picture i saw on a "ubuntu geek", or "ubuntu how to" site, so search.

---

### Post by markbuntu on 2008-06-19
Which ATI card do you have?

---

### Post by tyk on 2008-06-19
thank you pietjanjaap
that was helpful

---

### Post by Canis familiaris on 2008-06-20
> **markbuntu said:**
> Which ATI card do you have?

ATi Radeon X1250 (integrated)

---

### Post by Canis familiaris on 2008-06-20
Update: I am tring to  install ATI 8.6 drivers

---

### Post by Canis familiaris on 2008-06-20
In Catalyst 8.6, My monitor turns off and I could hear the sound only!

---

### Post by Canis familiaris on 2008-06-20
Well I have solved the problem.
(1) Passed the commands
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```
(2) Then installed the drivers by Hardware Drivers.

Before it I tried to install drivers by ATI and got correc login screen resolution by:
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
```

Hopefully one or more of these steps may solve the problem for anyone else.

---

### Post by Canis familiaris on 2008-06-20
However I still get flickering when playing movies in non-fullscreen mode when using compiz.

---

### Post by Canis familiaris on 2008-06-20
I solved the flickering problem by following this useful post.
> **markbuntu said:**
> If you want to fix the flickering widowed video problem you can edit the appropriate sections of your xorg.conf to look like this:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "off"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "DRI"
        Group       "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

Then run, in a terminal:

sudo aticonfig  --input=/etc/X11/xorg.conf

to write the changes to the actual ATI config file.

This will only work with the ATI driver 8.4 and newer. Also, you must have redirectfullscreenwindows checked in the compiz settings manager. 

The TexturedVideo "off" option can cause some full screen playback problems for older cards and slower cpus but will get rid of the windowed playback flickering. You can turn it back on for full screen high def playback if you need to.

ATI has recently made a great change in their commitment to linux, releasing source code to the driver writers groups, etc. They also seem to be committed to proprietary driver updates for newer cards about every six weeks which includes 3 weeks of testing before release.

They are aware of this problem with compiz and OpenGL and are working towards a solution. The 8.5 and 8.6 drivers have a lot of improvements over the 8.4 in the repos. The screensaver problem is fixed. The Compiz problem will be fixed soon. 

I expect that by the fall, ATI will be at least comparable to Nvidia.

---

### Post by Canis familiaris on 2008-06-20
I hope in the future just setting drivers of ATi and compiz would not be so difficult in the future.

---

### Post by archat68 on 2008-06-29
i have the same ATi IGP card.
When I try  "sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768"
I get:
Found fglrx primary device section
Nothing to do, terminating.
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.

When I use:
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
I get:
Package `linux-restricted-modules-2.6.24-18-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-restricted-modules-2.6.24-18-generic is not installed

I'm a complete newbie. Plss help

---

### Post by Canis familiaris on 2008-06-30
> **archat68 said:**
> i have the same ATi IGP card.
When I try  "sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768"
I get:
Found fglrx primary device section
Nothing to do, terminating.
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.

When I use:
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
I get:
Package `linux-restricted-modules-2.6.24-18-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-restricted-modules-2.6.24-18-generic is not installed

I'm a complete newbie. Plss help

Did you try installing the restricted kernel modules.

```
sudo apt-get install linux-restricted-modules-`uname -r`
```

Also the ` is not ' ` before uname -r is the key left of key 1 and over Tab.

---

### Post by markbuntu on 2008-06-30
I noticed after I installed the new driver that a few minutes later Update Manager informed me that it had a few updates for me and it turned put that they were the updates to the restricted modules. This was with the -18 kernel. 

When I updated to the 8.6 driver while on the -19 kernel I waited a few minutes after the install and sure enough, Update Manager had restricted module updates for me. So now, after installing a new driver, I give Update Manager a few minutes.

---


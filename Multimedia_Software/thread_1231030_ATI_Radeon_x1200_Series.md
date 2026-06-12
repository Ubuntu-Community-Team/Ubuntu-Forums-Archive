---
title: "ATI Radeon x1200 Series"
date: 2009-08-04
forum: Multimedia Software
---

### Post by paintedrealms on 2009-08-04
I think I solved the problem.  I use Jaunty edition or aka 9.04. My computer is a Dell Inspiron 1721 which uses the ATI Radeon x1270. At first when I was watching a movie, I had a flickering problem. also when I played video games on it like Adanaxis, the graphics would be real slow jumping frames. i think it refreshed every couple seconds.  that does no good when you are in the middle of blowing up a ship and you can't see him because your system is skipping frames.

Anyway to fix the problem, I started by taking the advice of Giantoz (thank you) and I got graphics driver and it gave these commands:

```

sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-ati

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install

```

I still needed more to go off of so I went in to my etc/X11/xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

and changed my xorg.conf file to look like this:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver "radeonhd"
	Option "RenderAccel" "on"
 	Option "AccelMethod" "XAA"
 	Option "AGPMode" "4"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
So now I have better resolution and I tried Adanaxis. SMOOOOOOOOTH!  I can actually play 3d games now and watch my movies. life is beautiful.

UPDATE:   I have seen a few of you have issues still with the problem.  I am pretty sure that if you switch radeonhd to simply radeon then it should correct the problem.  I use the radeonhd since mine is an hd card.  Still there are some issues still currently in the works and I know the kinks are still being streightened out.

---

### Post by zeusz4u on 2009-08-19
Hi,

I have a Radeon Xpress 1150, i tried all the steps tou provided, but after i changed x.org.conf and restarted x it said "unable to load module radeonhd", and i had to delete that line from xorgconf. Have you got any ideas what else could i change to fit my card as well?? I've just posted on another thread on this forum [http://ubuntuforums.org/showthread.php?t=1137467&page=5](http://ubuntuforums.org/showthread.php?t=1137467&page=5). While compiling those drivers i didn't get any error message... What else could the problem be??

I tried EXA instead of XAA, without loading the module, but the same... Or even with AGPMode 8... nothing changed. I have to mention that i'm experimenting on a live cd, but after restarting the xserver it should work this way as well. Please provide some help, i've posted my problems in the thread mentioned before, even on page 4, not only page 5.

---

### Post by juliocvaldez on 2009-08-26
Thanks a lot paintedrealms! I followed all your instructions. When I rebooted I got the graphics error. I chose to use default settings. I thought I was doomed again but when Ubuntu started I was shocked to see how good everything looked and sure enough compiz worked! By the way I'm running a Toshiba Satellite A215 S4747 with Jaunty.

---

### Post by Yellow Pasque on 2009-08-27
> Driver "radeonhd"
should be:
```
Driver "radeon"
```
Although you could try the radeonhd driver for this card as well: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by iTz Nicholas72 on 2009-08-31
Thank you so much this solved all of my x1200 issues.  The only problem with your tut is as stated above it needs to be radeon not radeonhd.

---

### Post by noobu on 2009-09-03
Any idea whether this will work with the ATI Radeon x600 card? I have a Dell Optiplex GX620 (pentium 4, 2 G memory) with Ubuntu 9.04. 

With the open source drivers, I notice lockups when I play 3D games like Alien Arena. The proprietary drivers don't work at all.

---

### Post by Yellow Pasque on 2009-09-03
noobu: You can certainly try building the latest ati driver, but there's no guarantee it will fix your problem.

---

### Post by zeusz4u on 2009-09-04
Try the open-source drivers, as discribed here: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

There's a script, and you may run it from a live-cd so you can test if it gives you any 3D improvement. It helped me. I have a Radeon Xpress 1150, and is no longer supported by ATI. With the stock radeon drivers i had about 300-350 FPS in glxgears (that means, all games unplayable, no GoogleEarth etc.), but as i tried the xorgedgers driver (it's the latest MESA driver, however it's in development stage, so sometimes you may have stability issues) , but it gave me at about 700 FPS in glxgears, and that means double of the original stock jaunty driver. Google-earth still sucks, cause it's very slooowwww. However in Extreme Tux Racer i had about 30FPS, so it's playable, you just have to disable some visual effects. I hope they're gonna make those open-source radeon drivers better in the near future, even before the release of Karmic, because this issue makes me use still the Intrepid release...

---

### Post by stark222000 on 2009-12-08
when i get to the

sudo make

i get this return. what do i do?

make: *** No targets specified and no makefile found.  Stop.

---

### Post by Yellow Pasque on 2009-12-08
The autogen script should create the Makefile, so you probably didn't run that. 
If you just want the latest version of the open-source ati driver, the easy way is to grab it here: [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

---

### Post by malleus74 on 2010-01-02
Does anyone know if Karmic handles x1200 better? I'm still sitting here with Intrepid because I want the 3D capabilities for WoW and a few other things...

---

### Post by Yellow Pasque on 2010-01-03
> Does anyone know if Karmic handles x1200 better?
You're not going to play WoW with the R500 open-source drivers (not yet anyway).

---

### Post by DoctorPooHead on 2010-10-20
Trying this under Lucid on a Thin Client with an ATI x1250. I'm somehow stuck.

After putting in 

```
sudo ./autogen.sh --prefix=/usr --enable-dri
```

I get this in return.

```
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
configure.ac:36: error: xorg-macros version 1.8 or higher is required but 1.5.0 found
/usr/share/aclocal/xorg-macros.m4:39: XORG_MACROS_VERSION is expanded from...
configure.ac:36: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
```

When trying to update xorg-macros though, I am told I have the latest version. Am I missing something here? :confused:

---

### Post by Mark Phelps on 2010-10-20
Not sure what you're trying to do, but current Xorg versions will not work with the proprietary drivers that used to work with your card, and the current drivers that do work with current Xorg versions won't work with your card.

So, you have to use compatible drivers and Xorg versions.

Not sure, but I believe Xorg 1.8 is too new to work with the older ATI drivers.

---

### Post by Yellow Pasque on 2010-10-20
> **DoctorPooHead said:**
> Trying this under Lucid on a Thin Client with an ATI x1250. I'm somehow stuck.
If you're trying to build latest mesa, you're much better off using the xorg-edgers PPA.

---

### Post by DoctorPooHead on 2010-10-20
> **Mark Phelps said:**
> ....
So, you have to use compatible drivers and Xorg versions.

Not sure, but I believe Xorg 1.8 is too new to work with the older ATI drivers.

I was afraid that was the case. I've been trying to get hardware acceleration working for the machine in an attempt to get XBMC running. 

I followed a nicely written [guide (http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#The_Options") which already suggested to jump back to Hardy.

> **Temüjin said:**
> If you're trying to build latest mesa, you're much better off using the xorg-edgers PPA.

Edgers PPA did work,.... but couldn't offer the acceleration required to run XBMC.


I do know that ATI dropped support for a range of cards/hardware, including this particular one. I figured I'd give it a shot anyway.

Thanks for the feedback guys. I really appreciate it.

---


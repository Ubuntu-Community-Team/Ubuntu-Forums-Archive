---
title: "(Fixed) ATI Radeon x1200 Series Screen Flicker"
date: 2009-09-01
forum: Multimedia Software
---

### Post by iTz Nicholas72 on 2009-09-01
Hey it took me a LONG time to find a solution that actually worked but today I finally found it but there was a small problem so I fixed the issue and I'm posting a new solution/tutorial.

**[SIZE=4]I want to give paintedrealms and Giantoz 100% of the credit for doing the actual work.[/SIZE]**

Step 1 - Enter below commands into Terminal
```
sudo apt-get install build-essential autoconf automake libtool pkg-config git-core

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev

cd xf86-video-ati

sudo ./autogen.sh --prefix=/usr --enable-dri

sudo make

sudo make install

```Step 2 - Enter the following commands into Terminal

```
sudo gedit /etc/X11/xorg.conf
```Step 3 -

Edit the .conf file and make it look like this:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver "radeon"
    Option "RenderAccel" "on"
     Option "AccelMethod" "XAA"
     Option "AGPMode" "4"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

Then restart your PC and you should be set.

Once again I take no credit all I did was change "radeonhd" to "radeon" in the xorg.conf file.

Hope this helps someone...

---

### Post by mkuangel on 2009-10-17
I followed your guide  glxgears and all 3D works fine but all players when I start playing some video stop working and closing 
I have Toshiba Satellite A215-S5822 with Ati radeon X1200 
Ubuntu Karmic Koala 
Please help

---

### Post by tecwizrd on 2009-10-21
What step goes between these two pieces of code?

CODE:

sudo apt-get install libdrm-dev x11proto-gl-dev mesa-common-dev xutils-dev x11proto-xf86dri-dev x11proto-fonts-dev x11proto-randr-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev x11proto-render-dev xserver-xorg-dev


##fixed: 

git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-ati

## end


cd xf86-video-ati

I do not have a directory "xf86-video-ati". :)

---

### Post by antonius on 2009-11-08
And this, of course, disabled any sort of video playback.  Damn it.  I did enjoy the screen not flickering for a few minutes though.  Reminded me of the good ol' days when everything worked.

---

### Post by miltonlaufer on 2011-03-03
I've solved this problem. Follow the steps that I mention here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665233](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665233)

---


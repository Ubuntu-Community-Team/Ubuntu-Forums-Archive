---
title: "Help, Scrambled Display after attempting to install ATI drivers."
date: 2008-09-10
forum: Multimedia Software
---

### Post by Buttons840 on 2008-09-10
I have Ubuntu 8.04, the latest version.  I really don't know much about Linux, but I'll lean by using it.

I have a HD 4850 ATI card and I attempted to fallow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

[SIZE="1"]> This will install the current driver in Ubuntu's repository. It is older than the one AMD has released, but will be supported by the Ubuntu people. Catalyst 8.3 is in the repositories.

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

The second line may not be necessary as you may already have restricted modules installed. Run it just in case. If the third line fails, you probably don't have the restricted repository enabled. See Pre-Installation.

After this, you'll may need to edit Xorg.conf:

sudo gedit /etc/X11/xorg.conf

In the device section, if it is not already there add:
File: /etc/X11/xorg.conf

Driver "fglrx"

Then to make sure Xorg is set up correctly, you'll have to let aticonfig "initialize" it:

sudo aticonfig --initial -f

After this you should be able to restart your computer and have the driver working. To test type

fglrxinfo

into a terminal. If the vendor string is not ATI, but Mesa, check #Removing Mesa drivers

...

 Removing Mesa drivers

If fglrxinfo reports that Indirect rendering by Mesa is in place, even though you have installed ATI driver, check:

    * Remove the package xserver-xgl. 

    sudo apt-get remove xserver-xgl

    Explanation: If you installed this previously in order to make compiz work, it will not allow direct rendering on your display. You can check out if this is what it causing the problem by running 

    DISPLAY=:0 glxinfo | grep render

    If it returns an ATI renderer, it means that xgl is being displayed indirectly on the display 1. (Taken from [1]) 

    Warning: This might make your compiz stop working as it is configured to use XGL. A solution might be to run the Envy script in order to configure compiz. Or, if Compiz stopped working due to "Composite" problem, check that the following is set in the /etc/X11/xorg.conf[/SIZE]

I attempted to reboot, just to see what would happen and now my display is all scrambled.  It covers the top half of the screen and you can tell the mouse and everything is there, but just not displayed on the monitor properly.  A normal monitor displays like this:

111111
222222
333333
444444
555555

Mine is going:

111122
222333
445555

I don't know where to even begin.  I've been looking around for others with this problem, but I have not found anything.  Any help is appreciated.  Is there a save mode or a way to get to a terminal prompt where I can reset the display settings?

---

### Post by 080711jk on 2008-09-10
[**&#21943;&#27849;**](http://www.music-water.com/index.asp)&#33402;&#26415;&#31574;&#21010;&#12289;[**&#21943;&#27849;**](http://www.music-water.com/index.asp)&#25928;&#26524;&#35774;&#35745;&#12289;[**&#21943;&#27849;**](http://www.music-water.com/index.asp)&#24037;&#31243;&#35774;&#35745;[**&#21943;&#27849;&#24037;&#31243;**](http://www.music-water.com/gc.asp?id=64)&#12289;&#25216;&#26415;&#24320;&#21457;&#12289;&#21152;&#24037;&#21046;&#20316;&#12289;[**&#21943;&#27849;**](http://www.music-water.com/index.asp)v&#23433;&#35013;&#35843;&#35797;&#21644;&#36816;&#34892;&#32500;&#25252;

---

### Post by Buttons840 on 2008-09-10
Is there anyway to reinstall the Mesa drivers?

Also, I failed to mention that the display is fine at the Ubuntu splash screen (where it says Ubuntu with the orange loading bar).

I suppose I could always reinstall, but that's not really practical, and I don't learn anything new from that.

Thanks.

---

### Post by s.stefansson on 2008-09-18
Hi man,

I'm in the exact same situation. New to Linux and Ubuntu. Installed 8.04 last week and today I followed the exact same installation guide to the ATI drivers. Guess what? Now my screen is scrambled exactly as you described!

I'm also using Ununtu 8.04 and an ATI HD4850.

Did you fix this somehow?

BR
Stefan

---

### Post by Juvencio on 2008-09-18
my Nvidia driver would not instal i tryed every thing

try EnvyNG ATI/NVIDIA driver installer

How do I Install EnvyNG?

> [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by s.stefansson on 2008-09-25
I reinstalled Ubuntu and tried with EnvyNG. EnvyNG stated that my gfx was not supported, so I chose manual installation and the ATI 8.6 driver. When I rebooted i was asked to choose my display and resolution which I changed. The system however just booted in 800x600 and I am asked to change this each time i boot.

Is it impossible use a HD4850 in Ubuntu? :confused:

---

### Post by WWSmith36 on 2008-09-25
No need to reinstall.  At the login screen select the option/sessions and choose failsafe.

This you start x with the default vesa drivers.

---


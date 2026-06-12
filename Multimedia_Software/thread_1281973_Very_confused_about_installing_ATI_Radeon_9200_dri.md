---
title: "Very confused about installing ATI Radeon 9200 drivers"
date: 2009-10-03
forum: Multimedia Software
---

### Post by Mettel on 2009-10-03
Hi, I'm new to linux and I've been playing around with it since yesterday.

I've been with Windows since version 3.3 and with Mac for the last 2 versions and I've understood that the 1st thing you do when you set up a new OS is install new drivers.

My specific problem is that I'm trying to get a game running. However, from the 1st screen its a very good guess that the video drivers are out of date or wrong somehow. The graphics are very grainy and discolored and many things are simply black.

The first thing I did was to go to the ATI (now AMD) drivers site and download the latest driver. Well neither of the xfree86 ones work and when I try to open the xorg one I get the error message:

[B]Could not open
"fglrx64_6_8_0-8.28.8-1.x86_64.rpm"
[/B]
Archive type not supported.

I'm guessing that driver is too old to be supported by Ubuntu. I searched around for a work around and on these forums I found a link to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). But, almost halfway down the page it tells you to type into the terminal:
```
sudo nano /etc/X11/xorg.conf
```After I do that I get this under 'device':

```
Section "Device"
        Identifier       "Configured Video Device"
        Driver           "vesa"
        Option           "UseFBDev"              "true"
EndSection
```Does this mean Ubuntu is not recognizing my ATI card?
If so how do I fix this?

I've been working on this all day and I'd be VERY grateful for any help

Card: ATI Radeon 9200

thanks

---

### Post by Mettel on 2009-10-03
I guess in less jumbled language, I'm just confused on how updating drivers works in Ubuntu, especially video drivers.

---

### Post by pme 72 on 2009-10-04
I checked the fglrx page, 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 

and it looks like the fglrx driver is not supported for ATI 9200 cards if you are using the latest Ubuntu release, Jaunty 9.04. You could try 8.04 Hardy Heron or 8.10 Intrepid Ibex if you need the proprietary fglrx driver.

It looks like your card may have 2D and 3D support with the Radeon Driver in Jaunty 9.04. 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


The FBDev driver does not provide any video acceleration 

[http://linux.die.net/man/4/fbdev](http://linux.die.net/man/4/fbdev)

You probably need to enable the Radeon Driver.

---

### Post by pme 72 on 2009-10-04
Here is a link to more information about installing video drivers with Jaunty 9.04:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by L_V on 2009-10-16
> **pme 72 said:**
> Here is a link to more information about installing video drivers with Jaunty 9.04: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Bloated, and completely useless for Radeon 9200.

lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)

**You don't need any package from ATI website**.
You need to be installed:
xserver-xorg-video-radeon xserver-xorg-video-ati libdrm2 libgl1-mesa-dri libgl1-mesa-glx
+  mesa-utils (optional for glxgears test)

Check you don't have any /etc/X11/xorg.conf file

Reboot => it schould work.

---

### Post by jravis on 2009-11-09
Im a new, non- savvy Linux convert. Had  a problem with radeon 9200.

I don't really understand any of what the procedure suggested by L_V does other than install some stuff on the machine with synaptic, but it solved the problem. So BIG thanks, L_V.):P

---


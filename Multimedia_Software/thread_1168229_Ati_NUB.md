---
title: "Ati NUB"
date: 2009-05-23
forum: Multimedia Software
---

### Post by pookiebear on 2009-05-23
Ok new linux guy here. got a video driver prob.
old laptop.
dell c610
p3 1ghz
512 megs ram. 
Running xubuntu

problem video seems slow.
no DRIVER listed in xorg.conf
LSPCI lists
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

seems like video is jerky slow. 

What should I do to get drivers for this or am I out of luck here?

Should I run the fglrx install?
sudo apt-get install xorg-driver-fglrx

Any thoughts would be appreciated. Thanks for the cool OS.

-pb

---

### Post by Mysticaly on 2009-05-23
Hi, this is a similar problem that I have in Kubuntu with Radeon x1950.

Read this explanation that I got in the Kubuntu forums, explained by ssri:

Your card is RV570 ([http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)). AMD/ATI dumped all R5xx cards to legacy support starting with Catalyst 9.4.  The last Catalyst version that supported your card and mine (Mobility Radeon x2300) was 9.3.  Unfortunately, Jaunty uses X server 1.6.0, which is compatible only with Catalyst 9.4 and above.  So, if you want to use Jaunty, you have to use the Opensource RadeonHD drivers (for ATI cards R5xx and above).  ATI will no longer issue proprietary drivers for our cards in default installs of Ubuntu Jaunty and above.  Yeah, you can downgrade x server 1.6.0 ([http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)) to the version on Intrepid and install the proprietary drivers that way.  But not many people reported their results with that method.  

Theres more information to be found in that thread here: [http://kubuntuforums.net/forums/index.php?topic=3104028.0](http://kubuntuforums.net/forums/index.php?topic=3104028.0) I'm pretty sure this information applies to Ubuntu as well.

For me installing the fglrx driver gave a black screen, and installing the Opensource RadeonHD driver gave some graphics tare, and made my screen out of focus (the refresh rate got messed up) and TV out (the reason I installed the driver) did not work at all. I had to uninstall the Open Source driver again.

I don't know if downgrading the x server to a previous version would be wise or not, I have not tried it yet, but I might.. Right now I'm stucked with windows thanks to the fact that I don't have any TV out, and I really don't want that, I want to be able to only run Linux (Kubuntu) and never have to think about dll files and windows in general again..

It's a real "show stopper" for me and many others

---

### Post by Melcar on 2009-05-23
You need the open source driver, radeon.  It should have been loaded by default, but in just in case do the following:

1. Open xorg.conf for editing

```
sudo mousepad /etc/X11/xorg.conf
```

2. Find the *Device* section and add the following line

```
Driver  "radeon"
```

3. Save and exit.  Reboot the computer

---

### Post by Mysticaly on 2009-05-23
> **Melcar said:**
> You need the open source driver, radeon.  It should have been loaded by default, but in just in case do the following:

1. Open xorg.conf for editing

```
sudo mousepad /etc/X11/xorg.conf
```

2. Find the *Device* section and add the following line

```
Driver  "radeon"
```

3. Save and exit.  Reboot the computer

Exactly what is the drivername of that driver ?
I would like to check if it's the same one that I manually installed

---

### Post by Melcar on 2009-05-23
**xserver-xorg-video-radeon**

It's already installed on Ubuntu, and it usually gets loaded when a compatible ATI card is detected.

---

### Post by Mysticaly on 2009-05-23
> **Melcar said:**
> **xserver-xorg-video-radeon**

It's already installed on Ubuntu, and it usually gets loaded when a compatible ATI card is detected.
Yes that is all well, but I might have misunderstood, but since X server 1.6 (or whatever version) and ATI dropping legacy support this driver will simply not work for the legacy ATI cards  ?

Or do I got this all wrong  ?

Anyhow, I just tried your suggestion by adding Driver "radeon" to the screen/device section and X would not even start...

My card is a ATI Radeon x1950 (I believe its a RV570 chip)

Come to think about it I should possibly have been adding radeonhd instead... I'll try that.. Possibly it will then use the open source drivers I manually installed, which where terrible to be honest.

---

### Post by pookiebear on 2009-05-23
> **Melcar said:**
> You need the open source driver, radeon.  It should have been loaded by default, but in just in case do the following:

1. Open xorg.conf for editing

```
sudo mousepad /etc/X11/xorg.conf
```2. Find the *Device* section and add the following line

```
Driver  "radeon"
```3. Save and exit.  Reboot the computer


Will this work for my 9 year old laptop? or was this for the other poster?

---

### Post by Melcar on 2009-05-24
> **pookiebear said:**
> Will this work for my 9 year old laptop? or was this for the other poster?


It should.


> **Mysticaly said:**
> Yes that is all well, but I might have misunderstood, but since X server 1.6 (or whatever version) and ATI dropping legacy support this driver will simply not work for the legacy ATI cards  ?

Or do I got this all wrong  ?

Anyhow, I just tried your suggestion by adding Driver "radeon" to the screen/device section and X would not even start...

My card is a ATI Radeon x1950 (I believe its a RV570 chip)

Come to think about it I should possibly have been adding radeonhd instead... I'll try that.. Possibly it will then use the open source drivers I manually installed, which where terrible to be honest.

That is the open source driver.  It does support your card (both 2D and 3D).  The driver is not fast, but you should be able to run things like Compiz and many open source games.  Also, it's only OpenGL1.3, so anything that needs OpenGL2.0/2.1 won't run (WINE for example).
The proprietary driver is called fglrx.  This one no longer supports your card.

---

### Post by pookiebear on 2009-05-24
that worked. Scrolling and flash video are much smoother now.

---


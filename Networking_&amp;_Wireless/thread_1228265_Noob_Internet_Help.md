---
title: "Noob Internet Help"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by EricaE on 2009-07-31
Hi. I just got through building my first computer and now I'm stuck. Linux is installed but it won't load any webpages. I have a wired connection. Cable. 
 
I've done a ping and it gets to ubuntu.com with 100% success, but whenever I go to firefox and type in the address it will not load. There's nothing that says connection failed or anything. Just a white page.
 
Could this have something to do with my graphics card? There is no integrated graphics on my motherboard, so I have a Radeon 4650 installed, but when I insert the driver's disc, it does not run but instead shows the icon on the desktop. Whenever I click launch.exe or setup.exe it gives an error message. When I tried to go through appearances and add 3d effects (thinking that maybe linux can tell the card is there), it wouldn't let me do that either. 
 
Please help. I really don't want to have to install vista.

---

### Post by jonobr on 2009-07-31
Hello


When you open a terminal window (applications -> accessories -> terminal)

and type w3m pingplotter.com

do you get something like what is attached?


When you put pingplotter in your browser what do you get?

Try also installing epiphany or seamonkey from synaptic and see if it gets the same result

---

### Post by EricaE on 2009-07-31
Thanks so much for helping me.

I did what you asked and all I received were blank screens.

I'm running the same internet on this computer, so I know the internet isn't down or anything.  I compared the ip on this computer to the one running linux and they are not the same.  Shouldn't they be the same?

---

### Post by jonobr on 2009-08-01
if you type in nslookup cnn.com or some other domain, does that resolve correctly?

---

### Post by t0mppa on 2009-08-01
> **EricaE said:**
> Could this have something to do with my graphics card? There is no integrated graphics on my motherboard, so I have a Radeon 4650 installed, but when I insert the driver's disc, it does not run but instead shows the icon on the desktop. Whenever I click launch.exe or setup.exe it gives an error message. When I tried to go through appearances and add 3d effects (thinking that maybe linux can tell the card is there), it wouldn't let me do that either.

Since you can load up XWindows (ie. Gnome desktop) there's some driver handling your card and it will be able to render text and pictures on websites perfectly well.

The driver disc won't work, because it only has Windows software and that doesn't work on Linux. The easiest way to install proprietary drivers in Ubuntu is going to System / Administration / Hardware Drivers and enabling the graphics drivers from there. It has a version that Canonical (company behind Ubuntu development) has deemed worthy for your current version of Ubuntu. Also, you can ask for help on the [Multimedia & Video forum]("http://ubuntuforums.org/forumdisplay.php?f=334"), if you run into trouble with those. And [here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")'s a helpful page on how to install the latest (ATI published Catalyst 9.7 about a week ago) version manually, if the older one doesn't suit you.

3D effects most likely aren't working, since the default driver is fairly simple and doesn't support them.

---


---
title: "Nvidia installation issues"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by ebaymarcaro on 2007-04-13
Sorry for another seminewbie post about the nvidia driver. I've followed various HOWTO guides on this forum (and others) for nvidia driver installation. All have led to my GUI interface breaking. I'm sure many people are tired of these posts, but I'm not finding any solutions through the guides.
 
Here's my situation:
OS: Ubuntu (Dapper)
Graphics card: Nvidia Geforce 7900 gs
Tried installing via: Gnome and KDE
I've checked to make sure my device is "nvidia" not "nv". 

I've tried four times now and all have led to the same issue of the gui interface not working. When I try installing the most recent Nvidia driver in Gnome, I get a message saying that it can't install the driver because x-server is already running (I'm assuming this means I have to run from command line not within gnome gui?). 
The second attempt of installing under gnome, the driver installed (partially). When I loaded the Nvidia window, it said the glx was not properly installed.
When I tried installing in KDE, it works...until I restart. Then Ubuntu just hangs at the loading screen.

Do these problems sound familiar to anyone?
I am thinking about starting fresh (possibly installing a fresh latest version of Ubuntu). After this, what should I install prior to trying to install the nvidia driver? 
I'm assuming that if I have both gnome and kde installed, i still only need to install the nvidia driver once (are there any special configurations if I want both gnome and kde?)

On a related note, when I installed kde, upon rebooting I get an error message when the login screen loads. It says cannot find theme (includes directory location). I'm assuming that I should copy some theme files into this directory, I just don't know what files i need).

I'd appreciate any advice / answers to my many questions. Thanks!!!

---

### Post by josesanders on 2007-04-13
I recommend starting fresh and using Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ebaymarcaro on 2007-04-13
I have already tried envy. Same results (just envy automates it for me :) ).
thanks for the suggestion though

-- see a post from 30 mins ago with a howto guide to install the nvidia driver with the lastest versions. I'll give this a try and see if it works---

---


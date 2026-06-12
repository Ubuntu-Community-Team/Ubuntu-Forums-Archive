---
title: "Flash Player Problem"
date: 2009-01-11
forum: Multimedia Software
---

### Post by diamondjim08 on 2009-01-11
Video streams on Yahoo do not play; movies on surfthechannel do not play; most Youtube movies do not play.  In short video streams on web sites do not play.  Right click on the blank screen and you get "Movie not loaded" from Adobe flash. 
DVD payer works fine.
I've installed all of the Codecs/packages I can find that are recommended from "Comprehensive Multimedia How to" but no success.
This is Xubuntu 8.10 OS fresh install trying to get it fully opreational.  I've done 2 Ubuntu 8.10 systems in the last month with little trouble.
Help! :(

---

### Post by mikewhatever on 2009-01-11
What's the output of <dpkg -s flashplugin-nonfree>? Post a link to the howto you followed.

---

### Post by diamondjim08 on 2009-01-11
Hi Mike,
Thanks for the comeback!  I've tried everything on my own but keep going in circles. Firefox keeps saying "movie not loaded" with black screens and the "Manage Content" window keeps suggesting that Flash be installed.
Here is the output of the terminal command:
diamondjim@diamondjim-desktop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 10.0.15.3ubuntu1~intrepid1
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (<< 6), libflashsupport, xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player ([http://www.adobe.com](http://www.adobe.com))
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
diamondjim@diamondjim-desktop:~$ 
Also, I checked the conflict listed in the output but synaptic does not list these as installed - so no conflict(?)
Very frustrating!!!!!!!!!!!!!!!!!
Thanks,
<> Jim

---

### Post by mikewhatever on 2009-01-11
It looks like flash is installed. Can you also post the outputs of the following:
dpkg -s gnash
dpkg -s swfdec-mozilla

---

### Post by diamondjim08 on 2009-01-11
Forgot the link:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
This is the Unbuntu Forums, Comprehensive Multimedia & Video How to,
Part 1/5 Essential Packages, Xubuntu section
Thanks,
<> Jim

---

### Post by Pete7 on 2009-01-11
I was having trouble playing some X games that were in .swf (Shockwave video). I made a disc and took them to work since I'm not horribly fond of the machine there. Windblows wouldn't play them because It thought they were too risky. A co-worker suggested opening them with Mozilla's Firefox.
Worked like a charm. 
For some reason Firefox opens most of the Adobe flash apps. on my machine.
Pete, Newbie, Denver

---

### Post by diamondjim08 on 2009-01-11
Ok Mike,
diamondjim@diamondjim-desktop:~$ sudo dpkg -s gnash
[sudo] password for diamondjim: 
Package: gnash
Status: purge ok not-installed
Priority: optional
Section: utils
diamondjim@diamondjim-desktop:~$ sudo dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: purge ok not-installed
Priority: optional
Section: utils
diamondjim@diamondjim-desktop:~$ 

These two not installed.

---

### Post by diamondjim08 on 2009-01-12
Good morning Mike,
Got the blasted thing fixed! Here is what I did:
Ran in circles for a couple of days!!!!!!!!!
Decided to remove firefox, ubufox (config files), firefox branding, flashplugin-nonfree in that order using Synaptic. Synaptic automatically removed dependencies. Then installed firefox, et al with Synaptic installing dependencies. BUT the last install was flashplugin-nonfree. I rebooted after each install and after flash install.
My test was Yahoo news videos and they loaded and played perfectly!!!! So there must have been some kind of "wild hair" in the previous installs.
Which brings me to my question about these multimedia codec installs: There must be a better way to do this?!
I've built 3 Ubuntu computers computers in the last 3 weeks and each one has had a different protocol and problem - this last one being the difficult one with flash. I think the "Comprehensive Multimedia & Video" in the Ubuntu Forums is the best BUT I think the sequence of these installs is very important so that crap like my problem is minimized.
Is my hunch correct and do you have a recommendation about this?
Thanks for your attempt and time to help me!! It is greatly appreciated. BTW, all 3 of the computers run flawlessly on Ubuntu!

Thanks again,
<> Jim

---

### Post by mikewhatever on 2009-01-12
Hey diamondjim08, glad it worked and thanks for the update. I don't know what the problem was, but suspect that reinstalling one or several of the packages got it fixed. I also don't know if the order of installations matters (don't think it should). The way I usually install codecs is by trying to play a file in Totem, clicking ok to search for codecs, and then installing whatever is found. It's easy, and I can't remember ever having problems. Try it next time you have a fresh installation. The only exception is the stuff from Medibuntu, but ever since I realized I only need a package or two from there, I stopped adding Medibuntu to the list of repositories.

---


---
title: "thinliquidfilm installation trouble"
date: 2009-06-29
forum: Multimedia Software
---

### Post by SPARTAN-118 on 2009-06-29
Hi, I am trying to install thinliquidfilm so I can encode/transfer videos to my iPod.

I am having difficulty with the install.py file. I drag it to the terminal, press enter, and always a different error shows up.
The first error had to do with python-qt3 not being installed; I easily fixed that.
Next, it was ffmpeg not being installed. I fixed that, however now it is reappearing, even though Synaptic Package Manager says it's installed.
This is the error message by thinliquidfilm installer:

> matthew@ubuntu:~$ '/home/matthew/Desktop/thinliquidfilm/install.py' 
*************************************
      installing thinliquidfilm
*************************************


-------------------------
Checking dependencies ...
-------------------------

pyqt is present

Couldn't find ffmpeg.  thin liquid film will not work without ffmpeg.  Aborting installation.
 I also tried sudo apt-get install ffmpeg, which led to it saying I had the newest version; however, I got this message:

> matthew@ubuntu:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
After using 'sudo apt-get autoremove' I get this:

> E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true
Not sure if the autoremove is linked to ffmpeg, but I did get past that problem ONCE.
When I did, it provided a link to THIS website: [http://liquidweather.net/howto/index.php?id=59](http://liquidweather.net/howto/index.php?id=59)
I followed the steps there, but, since (I'm assuming) the steps are for older distros, it didn't help. If anything, I think that's what caused the ffmpeg problem. Is there any way to correct this? (As in, undo the 

[LIST]
[*]sudo rm -f /bin/sh
[*]sudo ln -s /bin/bash /bin/sh
[/LIST]
commands?)

If not, is there another good encoding/tranfer program for iPod that *doesn't* require you to compile the source code or anything that advanced?

SPARTAN-118

---


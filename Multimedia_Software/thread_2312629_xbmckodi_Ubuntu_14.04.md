---
title: "xbmc/kodi Ubuntu 14.04"
date: 2016-02-05
forum: Multimedia Software
---

### Post by Ronald_hume on 2016-02-05
i have tried the install line using the apt command lines for kodi but the second does not recognise the ppa address and goes no further. i have a quad core q 6600  processor with 2 gb ram 500gb hdd and a graphics card. the system runs well in 64 bit mode i was trying to load kodi till this problem. the lines are below and the second is the one not running
e command line terminal and enter the following commands. Follow the prompts as you would any other software installation.  sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
 
this is some of what was attempted in the terminal

sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa

the terminal title is rshume@rshume-desktop:~  which is also the beginning of the command line
i have also tried this on the command line 
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main i386 Packages
the latter says no such file or directory
 
the former says cannot add ppa please check that the ppa name or format is correct.

 what am i doing wrong since i know this is a relatively simple syntax type error?


solution was a simple syntax error xmbc was used not xbmc... easy fix as long as python does not give any problems on reboot

---

### Post by papibe on 2016-02-05
Please don't reply on old threads: [http://ubuntuforums.org/showthread.php?t=2259512](http://ubuntuforums.org/showthread.php?t=2259512)

**Moved** to its own new thread.

---

### Post by Bucky Ball on 2016-02-06
Just wondering why you're using a third-party repository. XBMC is in the Software Centre. Best to install it from there. The version, in 14.04 LTS, is 2:12.3. May be a newer version in a newer release. Won't make a lot of difference in the end. The newer versions of xbmc are really kodi anyway and you'll probably find that's what you'll get.

---


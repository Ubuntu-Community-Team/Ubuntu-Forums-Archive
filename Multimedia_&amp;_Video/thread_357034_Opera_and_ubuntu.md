---
title: "Opera and ubuntu"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by sn0m on 2007-02-09
I am trying to install plugins for opera, it is asking me to install motif, but when i ./, ubuntu wouldn't let me, what's goig on here, anyone has got experience with opera.
ta
sn0m

---

### Post by nalioth on 2007-02-09
You'll want to find "libmotif3" in your package manager and install it.

---

### Post by sn0m on 2007-02-09
can someone sort me out here
this is the output from terminal:

sn0m@sn0m-laptop:~$ cd ~/Desktop
sn0m@sn0m-laptop:~/Desktop$ ls
install_flash_player_9_linux  install_flash_player_9_linux.tar.gz
sn0m@sn0m-laptop:~/Desktop$ cd install_flash_player_9_linux
sn0m@sn0m-laptop:~/Desktop/install_flash_player_9_linux$ sudo./flashplayer-installer
bash: sudo./flashplayer-installer: No such file or directory
sn0m@sn0m-laptop:~/Desktop/install_flash_player_9_linux$ ls
flashplayer-installer  flashplayer.xpt  libflashplayer.so  Readme.txt
sn0m@sn0m-laptop:~/Desktop/install_flash_player_9_linux$ sudo ./flashplayer-installer 

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/opera
dir= /usr/lib/opera

ERROR: Opera is not supported.

---

### Post by jtapper on 2007-02-11
I installed flash-plugin for Opera like this:

1. stage installed the plugin for firefox:
# tar xvfz install_flash_player_9_linux.tar.gz
# cd install_flash_player_9_linux/
# sudo ./flashplayer-installer

then gave firefox directory: 
/usr/lib/mozilla-firefox
y to proceed in installation

Ok. So far so good.

Then opened Opera and navigated to preferences pressing ctrl+F12
Advaced tab -> content -> plugin options -> Change path

Added /usr/lib/mozilla-firefox/plugins there and it works.

No problems so far, I haven't got any other FF plugins though.

---


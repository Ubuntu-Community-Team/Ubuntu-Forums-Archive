---
title: "How to install Flash plugin?"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by bobetko on 2008-01-24
I am trying to install Flash 9. 
If I do through synaptic I get: md5sums error.

I tried to download rpm package and got a lot failed dependencies...

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I am not experienced enough to know what are those. And I don't understand if they really want us to use those downloads, what is wrong with a little READ.ME to explain what need to be loaded first?

I can't believe I am chasing Flash for 3 hours now.... Before it worked, I don't even remember how would I install it.... such a waste of time....

Any help is appreciated...

---

### Post by jfinkels on 2008-01-24
To install the Flash plugin, enable the 'multiverse' repository in "System > Administration > Software Sources", then open a terminal (Application > Accessories > Terminal) and type the following:```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

See here for some more info: [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

If you get an error message, let us know exactly what the output of the above command in the terminal is.

---

### Post by MrClearPore on 2008-01-24
> I am trying to install Flash 9. 

If you're using Firefox as your Web browser, you're better off installing from the source files.  These are the official instructions from Adobe:

Use the first option (Option 1: .tar.gz)
and download that file which is **install_flash_player_9_linux.tar.gz**

Using your console terminal, 'cd' into the folder where it's saved and type ```
tar xvfz install_flash_player_9_linux.tar.gz
``` A folder with the name **install_flash_player_9_linux** will be created.

'cd' into that folder and type ```
./flashplayer-installer
``` and follow the instructions.  The Flash plugin will be saved to ~/.mozilla/plugins by default.

Good luck.

---

### Post by bobetko on 2008-01-24
it doesn't work.

Bad md5sums.

It actually get installed, but it is old version, so youtube doesn't work.

---

### Post by bobetko on 2008-01-24
Thanks MrClearPore,

It worked....

---

### Post by WilYumJay on 2008-02-17
Hello All!  My first post, and of course as a n00b I am having trouble doing something that should be simple.  See terminal listing below.  I get to the point where it asks me for the installation path to install the plugin, and even suggests what appears to be a valid path on my machine /usr/lib/mozilla  BUT it errors out stating "WARNING: Please enter a valid installation path."

Can anyone please tell me what I am doing wrong?  Thanks to all in ADV. 

Using Gutsy 7.10 Ubuntu. 


terminal listing:

billn@red-dwarf:/tmp/flash/install_flash_player_9_linux$ dir
flashplayer-installer  libflashplayer.so
billn@red-dwarf:/tmp/flash/install_flash_player_9_linux$ sudo ./flashplayer-installer
[sudo] password for billn:

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



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla/plugins

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

---

### Post by jfinkels on 2008-02-18
I highly recommend, for easily installation and removal, following my instructions above and installing the flash plugin using apt-get or aptitude:```
sudo aptitude install flashplugin-nonfree
```

If that doesn't work, can you post the output of the command:```
ls /usr/lib/mozilla
```
and ```
ls /usr/lib/mozilla/plugins
```

---

### Post by MrClearPore on 2008-02-19
> billn@red-dwarf:/tmp/flash/install_flash_player_9_linux$ sudo ./flashplayer-installer
Can anyone please tell me what I am doing wrong? Thanks to all in ADV. 

```
./flashplayer-installer
```

You're running the command as root.  Remove the word **sudo** and run the installer again.  Alternatively, you can just copy/paste the file **libflashplayer.so** to your **~/.mozilla/plugins/** directory.  That's all the installer does anyway.

Good luck.

---

### Post by Bablefish on 2008-02-19
I found this command on a Ubuntu site and it worked for me, and before this I was running Flash 7.

copy and paste in terminal
 wget -c [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb

---

### Post by saucysuzie on 2008-03-06
Another newbie
Attempted to dl the first option with mrclearpore's instructions but nothing happened after i entered the second code and nothing happened. Are insturctions supposed to come up or do i haveto dig some more?
thanks!

---

### Post by aysiu on 2008-03-06
Please follow these instructions. It's a step-by-step tutorial with screenshots. It makes very few assumptions (it assumes you can copy and paste and click on things with your mouse).
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---


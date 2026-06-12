---
title: "[SOLVED] Adobe Flash"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by marenkar on 2007-07-28
I installed my flash player and this came out in Terminal:

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/admin/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n):

Where do I find xpti.dat? do I really need to remove it? cause i used the search and couldnt find it, and flash isnt completely installed.:confused:

---

### Post by RomeReactor on 2007-07-28
Hi. The **xpti.dat** file is in a hidden directory in your home folder: open Nautilus, press CTRL+H to show the hidden files and folders, then go into".mozilla/firefox/********.default" and there you should find the file. Use this command to find its exact location:
```
locate xpti.dat
```

Don't worry about deleting it, it will be generated again next time you open Firefox, and this is done so that flashplayer gets recognized by the browser, I think. Not sure, though.

Also, you should probably run the installer as root:
```
sudo ./flashplayer-installer
```

---

### Post by marenkar on 2007-08-02
Thanks

---


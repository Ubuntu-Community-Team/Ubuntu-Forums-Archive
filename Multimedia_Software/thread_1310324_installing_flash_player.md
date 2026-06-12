---
title: "installing flash player"
date: 2009-11-01
forum: Multimedia Software
---

### Post by glovo_guy on 2009-11-01
I innstalled flashplayer 9 for ubunutu 7.10 but at one step it gives me:

--------------------------------------------------------------------------------------------------------------------------- 
root@User-desktop:/home/abdoulghafar/Desktop/install_flash_player_9_linux# ./flashplayer-installer 

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
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla
dir= /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): 

--------------------------------------------------------------------------------------------------------------------------------
I am sure this the path were the mozilla is installed but it seems not recognize it. Could
someone help me ?

thank you

---

### Post by unamanic on 2009-11-01
[http://www.ubuntu.com/news/ubuntu-7.10-eol](http://www.ubuntu.com/news/ubuntu-7.10-eol)

First off you should move away from 7.10 then just 
```

sudo aptitude install flashplugin-nonfree

```


however assuming your on a 32bit distro it would go in /usr/lib/mozilla

---


---
title: "Major tearing in 10.10 with ATI"
date: 2010-11-19
forum: Multimedia Software
---

### Post by T-bone24 on 2010-11-19
Hi, I've always had kind of an issue with tearing in Ubuntu but today I got round to updating to 10.10 64 bit, and decided to try and do something about the tearing.  I followed this ([http://www.*****************/driver/articles/fix-video-tearing-with-amd-proprietary-driver-on-ubuntu-10-10.html](http://www.*****************/driver/articles/fix-video-tearing-with-amd-proprietary-driver-on-ubuntu-10-10.html)) to the word except on the line "sudo aticonfig -initial" where I had to use "sudo aticonfig --initial" for the xorg.conf to regenerate. It worked great to start with but after a reboot the tearing got terrible. the tearing I used to experience was multiple tearing lines at random heights that appeared momentaryly and could only really be noticed in fast moving scenes of films or games, but now I get just one tear line which starts at the bottom of my monitor and slowly moves up to the top of the monitor over a period of about 10-15 seconds, once it gets to the top it re-appears at the bottom and starts again, and the refresh difference on either side of the tear is at about 0.5 seconds it makes videos pretty much unwatchable.

My graphics card is an ATI Radeon HD 8500, and the AA on it supports up to x8 sampling where as the tutorial only says to go up to x4 (im unsure if this is because x4 is the max for most cards or because for some reason mid settings are better) but both seem to get the same result.

Also I'm using the proprietary ATI drivers and Catalyst Control.

Any help is really appreciated.

---

### Post by T-bone24 on 2010-11-19
I've just noticed for some reason the link to the tutorial doesnt work, so here is the bulk of it

> First make a backup of xorg.conf
[INDENT]*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup*[/INDENT]

If something goes wrong you can any time use backup of xorg.conf
[INDENT]*sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf*[/INDENT]Now delete xorg.conf
[INDENT]*sudo rm /etc/X11/xorg.conf*[/INDENT]

Now you need to generate new xorg.conf, you can do this by typing:
[INDENT]*sudo aticonfig -initial*[/INDENT]This will generate new xorg.conf.


Now type:
[INDENT]*sudo aticonfig --sync-video=on*[/INDENT]
This will enable vsync.




---


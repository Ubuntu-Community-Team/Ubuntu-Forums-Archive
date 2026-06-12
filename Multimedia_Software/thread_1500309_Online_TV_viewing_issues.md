---
title: "Online TV viewing issues"
date: 2010-06-03
forum: Multimedia Software
---

### Post by thestretchman on 2010-06-03
I have recently upgraded to 10.04 and now I can not view abc.net.au/iview programs. The first time I visited the site I was told to upgrade the Adobe flashplayer, which was all good for 1 day and now when I try to watch a show it will close Firefox. When I restart FF it asks me if I want to start a new session or continue with the last one.

Coincidently now some games that I have installed through the Software Centre (Neverputt,Billiard-GL, Foobilliard being the ones I have tried) won't play/load at all. Not all games, Tali and Barrage work no probs.

I have updated everything I have been asked to and FF is the latest version.

Other online sites ([http://ten.com.au/watch-tv-episodes-online.htm](http://ten.com.au/watch-tv-episodes-online.htm)) that use flash still work fine

---

### Post by lovinglinux on 2010-06-03
Your system is 32bit or 64bit?

---

### Post by thestretchman on 2010-06-03
I am pretty sure it is 32bit.

I installed Chromium and tried to open the player and Flashplayer crashed. At the moment I have left Fllashplayer uninstalled. Is there an alternative or an update?

---

### Post by lovinglinux on 2010-06-03
Grab the latest beta release of [FLASH-AID](http://flash-aid-extension.blogspot.com/). It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Additionally, make sure you don't have libmoon installed. This package is causing such crashes when viewing flash content.

If that doesn't help, then you could get the [latest beta flash version from Adobe](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc7_linux_060210.so.tar.gz) and extract it to ~/.mozilla/plugins. Don't run FLASH-AID after this, because it will remove any flash plugin from the  ~/.mozilla/plugins folder.

---

### Post by thestretchman on 2010-06-04
Nothing has worked.

---

### Post by lovinglinux on 2010-06-04
> **thestretchman said:**
> Nothing has worked.

The problem occurs only on ABC right? Other video sites work?

---

### Post by thestretchman on 2010-06-06
Yes just ABC Iview as far as I can tell, the Ch10 site plays no probs. But I haven't been to others.  My games are still not opening either.

When I use the Chromium browser and try the iview site it gives an error msg

The following plugin has crashed: /usr/lib/flashplugin-installer/libflashplayer.so

---

### Post by GROwen on 2010-09-17
Did you ever find a solution to this?

I've come across exactly the same thing, none of the recommendations have worked for me either. It also seems to only occur in full screen mode.

What a drag. Loved using iView and didn't run into a problem until this week.

Thanks for any help you can give me with this.

---

### Post by lovinglinux on 2010-09-17
I don't have access to ABC, so I can't even test it. If you are on 64but, I woud try the new flash plugin.

---


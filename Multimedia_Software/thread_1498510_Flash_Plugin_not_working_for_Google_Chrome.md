---
title: "Flash Plugin not working for Google Chrome"
date: 2010-05-31
forum: Multimedia Software
---

### Post by pbandy34 on 2010-05-31
I've just upgraded to Ubuntu 10.4 and installed Google Chrome... The flash plugin won't work for some reason.  I've installed it/uninstalled it a dozen times, but when I try to go to youtube in Chrome, it still tells me to install the plugin...

It works fine in Firefox.

Any thoughts?

---

### Post by lovinglinux on 2010-05-31
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by bungee_hamster on 2010-06-07
I tried Flashaid as firefox kept crashing when I was loading webpages with lots of ad boxes and videos and now I can't watch videos at all - get the dreaded message that I need to get the latest adobe flash player.
Almost ready to chuck my ubuntu box - total newbie, in need of help.

Ok - that's odd. tried the command line instructions & now I can watch videos but firefox still crashes when I load a music fanpage with ads, flashy stuff and videos. I assume there must be some kind of conflict but not sure how to find out what?

---

### Post by lovinglinux on 2010-06-08
> **bungee_hamster said:**
> I tried Flashaid as firefox kept crashing when I was loading webpages with lots of ad boxes and videos and now I can't watch videos at all - get the dreaded message that I need to get the latest adobe flash player.
Almost ready to chuck my ubuntu box - total newbie, in need of help.

Ok - that's odd. tried the command line instructions & now I can watch videos but firefox still crashes when I load a music fanpage with ads, flashy stuff and videos. I assume there must be some kind of conflict but not sure how to find out what?

Use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/) to block unnecessary flash content.

---

### Post by bungee_hamster on 2010-06-21
so I tried FlashAid but now I can't use the street view on Google Maps (in Firefox!)as it wants me to download Flash Player 10. Flashaid seemed to remove a load of stuff but also couldn't find various files and so didn't remove them. Any thoughts on why flash still doesn't work? What info do I need to check for?

---

### Post by lovinglinux on 2010-06-21
> **bungee_hamster said:**
> so I tried FlashAid but now I can't use the street view on Google Maps (in Firefox!)as it wants me to download Flash Player 10. Flashaid seemed to remove a load of stuff but also couldn't find various files and so didn't remove them. Any thoughts on why flash still doesn't work? What info do I need to check for?

Is it only Google Maps' street view that isn't working? Can you watch YouTube videos?

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by milochen on 2010-10-19
If all you want to do is to play flash on chrome,

You may try to install chrome extension easily to solve this problem.

More detail could refer here ... 

[http://milochen.wordpress.com/2010/10/19/play-youtube-easily-with-google-browser-in-ubuntu-10-04-64bits/](http://milochen.wordpress.com/2010/10/19/play-youtube-easily-with-google-browser-in-ubuntu-10-04-64bits/)

---

### Post by SpeedyGonsales on 2012-06-29
I have 2 plugins for Flash in Chrome:

> Name:	Shockwave Flash
Description:	Shockwave Flash 11.3 r31
Version:	11.3.31.109
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so


and

> Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/adobe-flashplugin/libflashplayer.so


First just stopped working on last update to Chrome 20, in Chrome 19 everything worked fine. I disabled first plugin and now I have working Flash. Hopefully that will be solved soon.

---

### Post by nothingspecial on 2012-06-29
Please create a new thread rather than bumping and old one to the top.

Closed.

---


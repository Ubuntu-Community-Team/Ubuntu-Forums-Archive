---
title: "REAL PLAYER just won´t install on my machine"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by ela04cz on 2007-07-11
I know it has been asked for hundred of times, but: I still cannot solve it!

I have tried to add the repositories to the synaptic ([http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main). Then I typed ¨sudo apt-get install realplay¨ and anything looks like that, the message said this package couldn´t be found!

I downloaded the bin file from realplay linux website (realplayer10GOLD.bin something), and use the chmod a+x command and then the ./realplayer10GOLD.bin command, the installation process was there, looks like everything was all right, but when finished, it just won´t appear anywhere near the application>multimedia!(I am a xubuntu 7.04). I also access the software through its directory /home/ela04cz/programfiles/realplayer and then click on the icon, nothing at all.

I also tried to install with the .deb file for several times ( i tried those method above for like 7-8 times!) Sometimes I can find the realplayer icon in application>multimedia menu, but when clicked on, nothing happened either.

I think I have tried every method mentioned in this forum for many times, it just won´t install properly. Someone please give me a hint for this, otherwise I need to switch between xubuntu and windows many times a day just to watch my rmvb movies!

p.s. I found each time after I install using the bin file ( and I created a new directory for the thing each time like realplayer, realplay, etc) the directory cannot be deleted! It said ¨permission denied¨something like that. So I end up having many rubbish in my programfiles directory. Can someone also tell me how to get rid of this bunks please?

Many thanks for anyone who read through this!

---

### Post by jeffisawesome on 2007-07-11
Well I know it works on gnome because I installed from the .bin just the other day.  If I recall with KDE you have to add it to your menu manually.  As far as getting rid of old stuff... have you tried synaptic?  Your permission is denied because you aren't root btw.  Run your file manager from terminal using sudo and it should allow you to delete stuff.

---


---
title: "i just want tv-output"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by Vlatko on 2006-08-11
i followed this, it seems like, great guide [http://www.ubuntuforums.org/showthread.php?t=98456](http://www.ubuntuforums.org/showthread.php?t=98456)  but it didn't work for me.

what i want is tv-output. i have no dvd player so the pc is my only option. that's the last thing i need to be perfectly satisfied with my ubuntu. i have a nvidia 6600gt, drivers installed via automatix, i also have xgl/compiz installed, running dapper with all the updates. i use a s-video cable to connect to my tv. the tv has a scart input so i use a scart connector to plug in my s-video cable. the cable works as it does so in windows.

i don't really care which tv out i have, twinview, clone, single tv-out....i just want tv-output. someone please help me. i'm new to linux and this is the only thing left that i REALLY need.

---

### Post by tseliot on 2006-08-11
Try this guide:
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

---

### Post by Vlatko on 2006-08-11
> **tseliot said:**
> Try this guide:
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)
none of the two methods from that guide worked. it seems i've gotten furthest with your guide. :(

---

### Post by tseliot on 2006-08-11
Try asking here then:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by kill_u on 2006-08-12
I try the method for ATI but without any effect. The X crashes many times and I restore a old xorg.conf. 
But there is a something strange in this guide &#8211; don't have a example how to install Xinerama.
I try with apt-get but have not effect.


*sorry about my english*

---

### Post by tseliot on 2006-08-12
> **kill_u said:**
> I try the method fot ATI but without any effect. The X crashes many times and I restoe a old xorg.conf. 
But there is a somthing strange in this quide – don`t have a examlpe how to install Xinerama.
I try with apt-get but have not effect.


*sorry about my english*
You can't install Xinerama.

The guide says that "**Xinerama is a feature of X** that overcomes this limitation by allowing multiple screens to be associated with each other and bound together into a single, unified "virtual screen."

If you have the Xserver then you have also Xinerama

---

### Post by kill_u on 2006-08-13
> You can't install Xinerama.


.... but I can't install my TV-out too. Any idea for Ati Radeon 9550 &#8211; manufactured by  Gigabyte. I really need this. I try a five or four different ways and my tv-out didn't work. After reboot until gnome starts the tv-out work and I have a picture on booth screens. After gnome start the second monitor(TV) turn to blank. One month ago I use a Slax LiveCD and the tv-out work perfect.   What can i do? Try a another distro?

---

### Post by Vlatko on 2006-08-13
obviously we are out of luck. which is a shame actually cause i really thought ubuntu had it all for me. i tried a lot of distros and this one was really the best for me, i don't wanna change anymore.

---

### Post by kill_u on 2006-08-13
No I don&#8217;t change the Ubuntu, I use it from two years and I&#8217; am very happy to work with Ubuntu, but I cannot complete migrate from windows.

---

### Post by Ziox on 2006-08-13
you can try the command line tool nvtv, there's the link: [http://sourceforge.net/projects/nv-tv-out/](http://sourceforge.net/projects/nv-tv-out/)

but I do not know how to compile from sources, so any pointers would be greatly appreciated...

---

### Post by Vlatko on 2006-08-13
> **Ziox said:**
> you can try the command line tool nvtv, there's the link: [http://sourceforge.net/projects/nv-tv-out/](http://sourceforge.net/projects/nv-tv-out/)

but I do not know how to compile from sources, so any pointers would be greatly appreciated...
i installed nvtv via synaptic. though my card is not supported with nvtv. :(

---

### Post by kill_u on 2006-08-14
I try [this]("http://www.kde-apps.org/content/show.php?content=43612&forummode=2&forumpage=0&forumexplevel=all") application for KDE and my TV-out doesn’t work again. It may help with your video card.

---


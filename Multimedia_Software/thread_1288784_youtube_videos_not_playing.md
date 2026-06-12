---
title: "youtube videos not playing"
date: 2009-10-11
forum: Multimedia Software
---

### Post by LindaV on 2009-10-11
I have Ubuntu 9.04 on my laptop. Most of youtube videos aren't playing. The space where the video should be is just black and there are no error messages. Some videos are playing fine tho. 
I thought this could be a flash plugin problem, so I installed newest shockwave and tried 
*sudo apt-get install flashplugin-nonfree *but neither helped.
Any sudgestions?

---

### Post by tuxxy on 2009-10-11
You only need flashplugin-nonfree for 32-bit installs.  If its 64-bit then you should be using the 64-bit flash plugin available here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by wojox on 2009-10-11
Look at the Flash opti part on here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by LindaV on 2009-10-11
It's the 32-bit install. 
I tried removing all plugins and then installing flashplugin-nonfree as the optimization and troubleshooting guide suggested, but it didn't help.

---

### Post by ikacer on 2009-10-12
here is a thread that may help:
[Comprehensive Multimedia & Video Howto ]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by garvinrick4 on 2009-10-12
sudo apt-get clean

Now reinstall from GUI or Terminal.

You just reinstall from your package cache over and over.

By cleaning out cache you can fetch a new package.

Never know sometimes it works.

---


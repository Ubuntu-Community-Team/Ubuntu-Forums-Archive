---
title: "ATI Radeon X1900 XT"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by zool on 2006-06-12
Hello,

I'm having a hard time trying to setup my system to get proper 3D acceleration on ATI Radeon X1900 XT. My system is a Pentium D 3.2GHz on an ASUS P5WD2 Premium motherboard. I have tried both methods described at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"), with no success.

It seems the installation of the fglrx driver is successful, and X loads fine using the new driver. However, here's the output of fglrxinfo:

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

From what I've seen, the video card type should be included in the "OpenGL renderer string", but mine isn't. When I launch glxgears, CPU load goes up to 99%. I guess this means there's no acceleration.

I've been searching all over the web for a solution, with no success - hence my plea for help. Any suggestions will be greatly appreciated.

Thanks.

---

### Post by Teroedni on 2006-06-12
Glxgears often ets the cpu work hard, regardless of the video card;)

Can you run blender?
And what about screensaver , do they work (like the atunnel one for example)


And try to run this game
[http://www.linux-gamers.net/modules/news/article.php?storyid=1263](http://www.linux-gamers.net/modules/news/article.php?storyid=1263)
If that work your surely have 3d accelleration;)

---

### Post by zool on 2006-06-12
> 
And what about screensaver , do they work (like the atunnel one for example)


The screensavers do work, but some of them run at a very poor FPS. I'm pretty sure there's no acceleration.

> 
And try to run this game
[http://www.linux-gamers.net/modules/news/article.php?storyid=1263](http://www.linux-gamers.net/modules/news/article.php?storyid=1263)
If that work your surely have 3d accelleration;)

I launched the game, and it runs (with poor FPS, again) - however, in the "Graphic Settings" window, it says the 3D device is "Mesa GLX Indirect". I guess this too means there's no acceleration.

---

### Post by Teroedni on 2006-06-12
Open a terminal and write this

```
sudo gedit /var/log/Xorg.0.log
```

Paste it all here or attach it as a file

---

### Post by zool on 2006-06-13
> 

```
sudo gedit /var/log/Xorg.0.log
```

Paste it all here or attach it as a file

I have attached the X.org log as well as the X configuration file.

I have looked into the log, but I didn't find anything that could shed some light on this. The fglrx module is properly loaded, it correctly recognizes the video adapter chipset (R580 7249), DRI initialization succeeds... still, no acceleration.

---

### Post by david ly-gagnon on 2006-10-20
Hi, I have the same problem as well. The same same thing as zool has. 

alchemist@black:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 2.0.5814

I should be seeing x1900 ? I just bought the card today !

Here's my xorg.0.log and xorg.conf 

Any ideas how to fix ????

thanks

---

### Post by david ly-gagnon on 2006-10-20
and here is my xorg.0.log
:)

---

### Post by david ly-gagnon on 2006-10-20
Has anyone been able to solve this problem, please let me know :)

---


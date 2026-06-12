---
title: "[SOLVED] Video, googleearth FLICKERING"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Belerophon on 2008-12-27
Hello.

I've just upgraded to Intrepid.

While on hardy, i always had problems with linux games (openarena for example) and google earth -- they flickered a lot. Google earth was impossible to use. 3d games were a problem too.

After upgrading to intrepid, openarena was playable! google earth is still flickering, but less! 

The problem is that now, my videos also flicker with totem movie player and vlc. The flicker only stops if I put them in full screen mode! Totem, for example, only stops having the problem after that time-out in which there still are visible menus in full screen mode. When menus totally disappear in full screen mode, the flickering stops completely.

I have a ATI X1600, compiz enabled...

Can anyone help me?

Thanks.

---

### Post by Belerophon on 2009-01-03
*Bump*

---

### Post by umechanism on 2009-01-06
Have you tried any of these suggestions in this thread?
[http://ubuntuforums.org/showthread.php?t=1023688&highlight=vlc+flicker](http://ubuntuforums.org/showthread.php?t=1023688&highlight=vlc+flicker)

---

### Post by LowSky on 2009-01-06
turn off compiz, simple as that

install fusion-icon from synaptic to control compiz formthe panel tray to make the change simply

---

### Post by Belerophon on 2009-01-07
Thanks umechanism and LowSky!

Disabling compiz, makes all good! However, I'd prefer not to have to disable compiz every time I want to make use of any of these applications.

With compiz turned on, this workes for movie player and rythmbox visualizations:
> 
Type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under Default Output, choose X Window System (no Xv).

However, googlearth and vlc continue to flicker!!

As for vsync, I used the ATI control center and put the slider to the right, like it is in the screen shot.

As for the last tip, I have intrepid, does xorg.conf still exists?



One way or another, the tips on the other forum and knowing that disabling compiz solves everything has been a great help!! Thank you both, umechanism and LowSky.
Please, if there is another to put things working with compiz turned on, please advice :D

Thanks

---

### Post by umechanism on 2009-01-07
Hey, glad it worked out for you.  Turning off effects seems to work well for me to.

---

### Post by Melcar on 2009-01-07
There is no other way around it at the moment.  You have to turn off Compiz if you plan to run any 3D and/or hardware accelerated videos, although some applications (mostly games) can work with Compiz as long as they're in fullscreen.

---

### Post by ubuntu-freak on 2009-01-07
Some games and Google Earth use OpenGL, so it makes sense to disable desktop effects when running them.
 
Also, you shouldn't disable Xv (Xvideo) if you like high quality video.

---

### Post by ubuntu-freak on 2009-01-07
> **Melcar said:**
> There is no other way around it at the moment.  You have to turn off Compiz if you plan to run any 3D and/or hardware accelerated videos, although some applications (mostly games) can work with Compiz as long as they're in fullscreen.

 
Same kinda post within a minute of each other! 
 
Great minds etc... ;)

---

### Post by Belerophon on 2009-01-08
> **ubuntu-freak said:**
> Some games and Google Earth use OpenGL, so it makes sense to disable desktop effects when running them.
 
Also, you shouldn't disable Xv (Xvideo) if you like high quality video.

Sorry, can you elaborate? They use OpenGL so I need to disable Compiz why?

---

### Post by ubuntu-freak on 2009-01-08
> **Belerophon said:**
> Sorry, can you elaborate? They use OpenGL so I need to disable Compiz why?

 
Cos' it's two separate instances of OpenGL, one managed by Compiz, the other by a game, application, screensaver etc, which causes flickering as they're overlapping each other. That's my understanding, anyway.

---

### Post by Redsunz on 2009-01-09
"turn off compiz, simple as that"
Yeah that worked for me. No more flickering now if Google Earth wasn't so slow.
I can't go into the menu and make sure open GL is clicked because the tool bar fonts are to small to read. I read the forum on that but I have a newer version and the config file is not the same name different location. In other words I could not find it.

---


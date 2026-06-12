---
title: "Nvidia drivers"
date: 2011-06-12
forum: Multimedia Software
---

### Post by andrea000 on 2011-06-12
wildmanne39 you have the nvidia 173 driver working and unity loads
and displays everything fine?if you don't mind me asking how did you
get it to work.My nvidia 173 driver would install but in additional
drivers it is saying driver installed but not currently in use and only
my wallpaper was showing nothing else.
Thanks

---

### Post by wildmanne39 on 2011-06-12
> **andrea000 said:**
> wildmanne39 you have the nvidia 173 driver working and unity loads
and displays everything fine?if you don't mind me asking how did you
get it to work.My nvidia 173 driver would install but in additional
drivers it is saying driver installed but not currently in use and only
my wallpaper was showing nothing else.
Thanks
Hi, the part about it not being in use is just a bug, if you activated it, it is really in use. In unity the desktop is blank only thing comes up is when you move your mouse to the left of the screen you should see the launcher, everything else is in dash, you can access it by clicking on the apps icon in the launcher, if you do not see the launcher on the left of the screen when you move your mouse all the way to the left of the screen then maybe your are in ubuntu classic, log out and click on user name and see if there is one that just says ubuntu at the bottom of the screen if there is click on it. if not put this command in the terminal and post the output back here.
```
/usr/lib/nux/unity_support_test -p
``` also did you do a clean install or did you upgrade?

---

### Post by andrea000 on 2011-06-12
Thanks for the quick answer

I ran the unity support test with the nvidia driver installed
and it said unity supported but the desktop doesn't show it's 
only my wallpaper I didn't know if there was something about 
how i was installing the nvidia driver.I also just installed
the nouveau Gallium 3d driver and it works a little better the
desktop shows but there is no icons on the launcher.I did a
clean install on 11.04.



Here is the output from the test the output is the same on both test.

> Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes




---

### Post by wildmanne39 on 2011-06-12
> **andrea000 said:**
> Thanks for the quick answer

I ran the unity support test with the nvidia driver installed
and it said unity supported but the desktop doesn't show it's 
only my wallpaper I didn't know if there was something about 
how i was installing the nvidia driver.I also just installed
the nouveau Gallium 3d driver and it works a little better the
desktop shows but there is no icons on the launcher.I did a
clean install on 11.04.



Here is the output from the test the output is the same on both test.
Hi, the output is good. You say you can see the launcher on the left side of the screen, but it is empty? It sounds like you might not have got natty installed all the way. Go to synaptic since you have installed more then one nvidia driver and make sure only one is installed. hit the windows key and see if the launcher comes out, if so if dash opens. Can you take a screen shot of your desktop for me?

---

### Post by andrea000 on 2011-06-12
I only have one driver installed it looks like a lot of
people is having this problem.I'm in ubuntu classic right
now but here is a [link]("http://img203.imageshack.us/f/screenshotnk.png/") that someone else has uploaded with
the same problem my launcher look just like this one.Compiz
running in classic mode runs good if that helps.

---

### Post by overdrank on 2011-06-12
No need to highjack the thread. Moved to its own thread. :)

---

### Post by garagestmarien on 2011-06-12
I have installed Unity 2D and everything is now running fine, I don't know if this helps. (As far as I understand, there is very little missing from using Unity 3D).
I also ran the above test and have this result:

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5900/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

What does not blacklisted mean? and can I solve this?

---

### Post by wildmanne39 on 2011-06-12
> **andrea000 said:**
> I only have one driver installed it looks like a lot of
people is having this problem.I'm in ubuntu classic right
now but here is a [link]("http://img203.imageshack.us/f/screenshotnk.png/") that someone else has uploaded with
the same problem my launcher look just like this one.Compiz
running in classic mode runs good if that helps.Hi, follow this guide and I think it should get unity working for you.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by wildmanne39 on 2011-06-12
> **garagestmarien said:**
> I have installed Unity 2D and everything is now running fine, I don't know if this helps. (As far as I understand, there is very little missing from using Unity 3D).
I also ran the above test and have this result:

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5900/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

What does not blacklisted mean? and can I solve this?
Hi, did you see the unity side bar when you first checked out unity from the livecd or usb stick? Have you installed the drivers for your card in additional drivers? That message you got says that your video card is not supported for unity but it might change if the drivers for your card are installed but I do not think that is the case.

---

### Post by jcd29 on 2011-06-13
> **wildmanne39 said:**
> Hi, the part about it not being in use is just a bug, if you activated it, it is really in use. In unity the desktop is blank only thing comes up is when you move your mouse to the left of the screen you should see the launcher, everything else is in dash, you can access it by clicking on the apps icon in the launcher, if you do not see the launcher on the left of the screen when you move your mouse all the way to the left of the screen then maybe your are in ubuntu classic, log out and click on user name and see if there is one that just says ubuntu at the bottom of the screen if there is click on it. if not put this command in the terminal and post the output back here.
```
/usr/lib/nux/unity_support_test -p
``` also did you do a clean install or did you upgrade?

How do you know it's in use though? Couldn't it be the open source driver working?

---

### Post by wildmanne39 on 2011-06-13
> **jcd29 said:**
> How do you know it's in use though? Couldn't it be the open source driver working?
Hi, if you go into additional drivers and you have a driver there to activate and you activate it, it really is in use, the part that says it is not in use is a bug if it is showing activated,but I was talking to her about her card not yours, your says it is not supported, does yours also show a green dot next to it and does it say activated, if so then it is and it is being used, now if you installed from another source also then you probably have two installed and that is a problem and you need to go look in synaptic and see and uninstall one of them, also you are suppose to start your own thread because what we say for one person might not be the answer for another, like I know hers is working because she can see the unity desktop, and I know it says yours is not supported because of the test you ran.

---

### Post by sikander3786 on 2011-06-13
> **garagestmarien said:**
> I have installed Unity 2D and everything is now running fine, I don't know if this helps. (As far as I understand, there is very little missing from using Unity 3D).
I also ran the above test and have this result:

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5900/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yeshttp://www.google.com.pk/
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

What does not blacklisted mean? and can I solve this?

Those cards which were a bit problematic with Unity were black-listed to run it but there is a workaround. See here on how to Force Unity to run on those cards.

[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

---

### Post by andrea000 on 2011-06-13
Well i installed unity 2d it works fine but I
would also like to run compiz I like the resize
windows it has.I was doing that back in 8.04
but they have a plug in for that now.I seen a
lot of post that seem to be running compiz with
unity 2d but it just don't work for me it makes
my desktop do all kinds of things.I guess I'll
wait and see if new driver updates to the open
source driver help or maybe try gnome 3.Does any
one know anything about gnome 3?I have been reading
a little and it seems to still have a lot of bugs.

Thanks

---

### Post by jcd29 on 2011-06-13
> **wildmanne39 said:**
> Hi, if you go into additional drivers and you have a driver there to activate and you activate it, it really is in use, the part that says it is not in use is a bug if it is showing activated,but I was talking to her about her card not yours, your says it is not supported, does yours also show a green dot next to it and does it say activated, if so then it is and it is being used, now if you installed from another source also then you probably have two installed and that is a problem and you need to go look in synaptic and see and uninstall one of them, also you are suppose to start your own thread because what we say for one person might not be the answer for another, like I know hers is working because she can see the unity desktop, and I know it says yours is not supported because of the test you ran.
Oh no dude, I think you maybe mixed up my post with another, heh. Because I don't have any card or problems right now, I was just curious about that case in particular, and wanted to know if the open source drivers could be the ones doing the work. Thanks :D

---

### Post by winger1312 on 2011-06-13
Noticed this when I ran compiz_check

Gathering information about your system... 
Distribution: Ubuntu 11.04 
Desktop environment: GNOME 
Graphics chip: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 
[COLOR="Red"]Driver in use: nouveau [/COLOR]
Rendering method: Nvidia 

Checking if it's possible to run Compiz on your system... 
Checking for texture_from_pixmap... [ OK ] 
Checking for non power of two support... [ OK ] 
Checking for composite extension... [ OK ] 
Checking for FBConfig... [ OK ] 
Checking for hardware/setup problems... [WARN] Something potential problematic has been detected with your setup: Warning: Detected driver is not on the whitelist.  Would you like to know more? (Y/n)

The problem is I am using Nvidia 173 driver, not Nouveau.  The only graphical issue I am having is that there are no Launcher Icons. If compiz is telling me its using Nouveau driver and proprietary it has to be a detection issue and not rendering issue. Could this be causing all of the Nvidia problems?  And are there any ways to fix this?  I am forcing Unity at start by the way.

---

### Post by wildmanne39 on 2011-06-13
> **winger1312 said:**
> Noticed this when I ran compiz_check

Gathering information about your system... 
Distribution: Ubuntu 11.04 
Desktop environment: GNOME 
Graphics chip: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 
[COLOR="Red"]Driver in use: nouveau [/COLOR]
Rendering method: Nvidia 

Checking if it's possible to run Compiz on your system... 
Checking for texture_from_pixmap... [ OK ] 
Checking for non power of two support... [ OK ] 
Checking for composite extension... [ OK ] 
Checking for FBConfig... [ OK ] 
Checking for hardware/setup problems... [WARN] Something potential problematic has been detected with your setup: Warning: Detected driver is not on the whitelist.  Would you like to know more? (Y/n)

The problem is I am using Nvidia 173 driver, not Nouveau.  The only graphical issue I am having is that there are no Launcher Icons. If compiz is telling me its using Nouveau driver and proprietary it has to be a detection issue and not rendering issue. Could this be causing all of the Nvidia problems?  And are there any ways to fix this?  I am forcing Unity at start by the way.Hi, I do not know, I am also testing the next release of ubuntu and right now it still shows the driver not in use, but I know it really is because if it was not we could not even see the unity desktop.

---

### Post by wildmanne39 on 2011-06-13
> **andrea000 said:**
> Well i installed unity 2d it works fine but I
would also like to run compiz I like the resize
windows it has.I was doing that back in 8.04
but they have a plug in for that now.I seen a
lot of post that seem to be running compiz with
unity 2d but it just don't work for me it makes
my desktop do all kinds of things.I guess I'll
wait and see if new driver updates to the open
source driver help or maybe try gnome 3.Does any
one know anything about gnome 3?I have been reading
a little and it seems to still have a lot of bugs.

ThanksHi, I think you might can fix unity if you look at the link in post #8. If you are happy for now, you can continue with unty 2d it is not bad.

---

### Post by andrea000 on 2011-06-14
I just updated the open source driver tonight and
am going to try what the link says so wish me luck.
The open source driver seems to work better with
unity 3d and it is twice as fast on gnome classic.

Do you know anything about gnome 3?

---

### Post by wildmanne39 on 2011-06-14
> **andrea000 said:**
> I just updated the open source driver tonight and
am going to try what the link says so wish me luck.
The open source driver seems to work better with
unity 3d and it is twice as fast on gnome classic.

Do you know anything about gnome 3?
Hi, most people are not happy with it unless they do a lot of extra tweaking and it can break your system. Unity and gnome3 can not be on the same system at the same time. It is totally redone from gnome2. If you put gnome3 on and want to get rid of it you have to reinstall unity to get it working right again, I have tried three times when gnome3 and unity first came out and it failed every time.

---


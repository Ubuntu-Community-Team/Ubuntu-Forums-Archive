---
title: "Resolution/Overscan Issues"
date: 2009-11-19
forum: Multimedia Software
---

### Post by danger pigeon on 2009-11-19
Not quite sure if this is the right category for this. I realize there are a lot of threads about overscan and resolution problems, but i've read a lot of them and very few offered any kind of solution at all. I have a 1080p monitor (LVM-37w3 if your interested) that has a native resolution of 1900x1080 but the highest resolution i can use in ubuntu is 1280x800. If i select a higher resolution, the edges of the screen get clipped off and i can't see the panels at the top or bottom of the screen.
 
Now i know it's not a problem with the TV or with my graphics card because when I run windows (i have a dual boot) i can run 1900x1080 no problem and it looks great. What can i do to fix this? I feel like im wasting my screen by using such a smaller resolution.

---

### Post by Bojanglez on 2010-02-26
I have the same problem on my 1080p screen using 9.10 and the latest proprietary nvidia drivers. All the menus are under the edge of the screen and all the fonts look massive, however the icons are the size you would expect. Any help in resolving this issue would be much appreciated.

---

### Post by Yhor on 2010-03-10
This is something I'm also having trouble with. ATI and Nvidia with a Hannspree 24.x'" display (I've used both ATI and Nvidia cards with prop drivers and free drivers, prop drivers have overscan issues and free drivers lack performance). 

Does anyone know the command to run at startup to resize with xrandr? If so, can you give instruction on how to put it into a start up file, please?

Further explanation...
My current gpu is ATI onboard HD 3300. I have been able to get the refresh rate to take by running in terminal```
xrandr -r 60
```*CCC had my refresh rate stuck at 25 hz and was unable to change via CCC. 

I've seen posts in other areas (other sites that I'm not 'comfortable with', and don't remember post location) that people have been able to fix overscan by using a similar command in a startup file. AFAIK, my monitor doesn't have an option to fix my issue as some TVs do, so if anyone can help with a xrandr command and a how to for putting it into a start up file, it would probably save a lot of people from experiencing hair loss, sleeplessness, turret's syndrome (sp?), among other stress related issues.;)

I'm pretty new to Ubuntu/Linux. I've used it in Wubi off and on for several years, but I didn't have these types of issues and I was using primarily for the fun of the software available. I'm now using it, being completely fed up with Windows, as my sole OS (9.04 Jaunty). Any help is greatly appreciated :D.

---


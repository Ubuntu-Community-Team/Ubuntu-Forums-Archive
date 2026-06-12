---
title: "permanant sound fix. kdm resolution. kdm theme"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by Latem on 2006-06-15
My first issue is regarding sound.  After upgrading to Kubuntu, my sound was gone.  The card seems to be detected same as before, and to the best of my knowledge settings were OK.  So I went onto IRC, and asked around.  A guy in #kubuntu asked me to do:

```
asoundconf list && amixer
```

He looked at the results, and then afterwards told me to do:

```
amixer set 'IEC958 Optical Raw' off && amixer set 'Front' on && amixer
set 'Wave' 80%,80%,on,on
```

This got me my sound.  However the issue is that every time I log in, I do not have sound, and I have to do this command.  Any permanant way of fixing this?  Also can someone explain to me exactly what this comand does? I am not sure what IEC958 Optical Raw, Front, and Wave refer to.

My second issue is quite simply, how can I change my kdm login screen resolution and possibly refresh rate.  Right now, my login screen resolution is quite bigger than my desktop's, and I would like them to be the same. 

I can't find anything in "System Settings" to control KDM settings.  For example I can't seem to find any GUI way of changing KDE theme.  I have to manually backup the current "kubuntu" theme in /usr/share/apps/kdm/themes, and then copy another folder named "kubuntu" in there, that has the theme I want.  Is there a settings module or something for configuring kdm.

Thanks

Latem

---

### Post by solderhead on 2006-11-19
> **Latem said:**
> 
My second issue is quite simply, how can I change my kdm login screen resolution and possibly refresh rate.  Right now, my login screen resolution is quite bigger than my desktop's, and I would like them to be the same. 

I can't find anything in "System Settings" to control KDM settings.  For example I can't seem to find any GUI way of changing KDE theme.  I have to manually backup the current "kubuntu" theme in /usr/share/apps/kdm/themes, and then copy another folder named "kubuntu" in there, that has the theme I want.  Is there a settings module or something for configuring kdm.

I am having the same problem.  The normal bootsplash theme works properly, but when KDM is started, it is initialized at a resolution that is higher than the resolution of the screen display.  When Xorg/KDE start, everything is normal.  This appears to be a problem that is limited to KDM.

When KDM starts, the KDM logon box is displayed in the middle of the screen, but if you wiggle the mouse, then you end up scrolling all over the place, and the KDM logon box moves as additional portions of the desktop are passed over the display.

It would appear that KDM is being initialized so that the size of the virtual desktop exceeds the size of the physical desktop.  As a result, when you move the mouse, the physical desktop moves about giving you a "porthole" view of the much larger virtual desktop.  It appears as if you are scanning the scene with a pair of binoculars.

I also find this to be a bit annoying, and I'd love to find out how to fix the problem.  Unfortunately, the title of this thread doesn't really draw the user to the second problem, so I doubt that it will draw many eyes to the problem.  Perhaps starting a new thread will help.

---

### Post by Funzo22 on 2006-11-19
> **Latem said:**
> My first issue is regarding sound.  After upgrading to Kubuntu, my sound was gone.  The card seems to be detected same as before, and to the best of my knowledge settings were OK.  So I went onto IRC, and asked around.  A guy in #kubuntu asked me to do:

```
asoundconf list && amixer
```

He looked at the results, and then afterwards told me to do:

```
amixer set 'IEC958 Optical Raw' off && amixer set 'Front' on && amixer
set 'Wave' 80%,80%,on,on
```

This got me my sound.  However the issue is that every time I log in, I do not have sound, and I have to do this command.  Any permanant way of fixing this?  Also can someone explain to me exactly what this comand does? I am not sure what IEC958 Optical Raw, Front, and Wave refer to.

My second issue is quite simply, how can I change my kdm login screen resolution and possibly refresh rate.  Right now, my login screen resolution is quite bigger than my desktop's, and I would like them to be the same. 

I can't find anything in "System Settings" to control KDM settings.  For example I can't seem to find any GUI way of changing KDE theme.  I have to manually backup the current "kubuntu" theme in /usr/share/apps/kdm/themes, and then copy another folder named "kubuntu" in there, that has the theme I want.  Is there a settings module or something for configuring kdm.

Thanks

Latem

For your first problem, your first problem by entering that command to run at login, I guess some would say to make a debian boot script, but it would be easier just to do this:

Go to system/preferences/session and go to startup programs and press add, then enter that command and next time you start your computer it will be fixed


Edit: I just realized your running kubuntu, and I dont know the exact way to do this in KDE, but it should be somewhere in the control center somewhere... maybe someone else who uses kubuntu can elaborate for you :)

---

### Post by solderhead on 2006-11-19
for the second problem, look here:

[http://www.ubuntuforums.org/showthread.php?p=1781004#post1781004](http://www.ubuntuforums.org/showthread.php?p=1781004#post1781004)

---


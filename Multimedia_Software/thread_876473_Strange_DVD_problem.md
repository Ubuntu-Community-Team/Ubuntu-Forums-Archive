---
title: "Strange DVD problem"
date: 2008-07-31
forum: Multimedia Software
---

### Post by nifty542 on 2008-07-31
Hi, all

Absolutely new Ubuntu user. Really, really want to migrate to Linux.

Have installed, downloaded (as far  as I can tell) all the necessary updates, but have a strange problem....

I can't access DVD menus, and when I start the DVD, it plays a random menu, in my case a version with commentary by the cast....

Sorry if this is elementary, I am very inexperienced with Linux

Regards

Nifty

---

### Post by nbayiha on 2008-07-31
Welcome to Ubuntu :) .
Let's get back to work , what do you mean by you can't access to the DVD , i mean do you have already Ubuntu installed. Are you using the system and you cannot watch a DVD movie is that what you mean ?

---

### Post by nifty542 on 2008-07-31
> **nbayiha said:**
> Welcome to Ubuntu :) .
Let's get back to work , what do you mean by you can't access to the DVD , i mean do you have already Ubuntu installed. Are you using the system and you cannot watch a DVD movie is that what you mean ?
Hi, Thanks for the very prompt reply. What I mean is, the dvd plays, but without access to the menu, and in my case, plays with a commentary from the cast ("Police Academy") which I know is an option in the main menu, but I am unable to access it.

Thanks for replying

Regards

Nifty

---

### Post by nbayiha on 2008-07-31
Ok dude try this.

I took it from this thread, [http://ubuntuforums.org/showthread.php?t=766683&highlight=DVD+player](http://ubuntuforums.org/showthread.php?t=766683&highlight=DVD+player) , and right here i just pasted the part i think you may find usefull.

For the best DVD playback in Ubuntu, including menu support, install the following packages:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

You can also use the Xine engine in Ubuntu (default engine in Kubuntu and Xubuntu) for video/DVD playback. This can be done without having to change the backend of Totem - just install an alternative GNOME frontend for Xine called Gxine (this is optional, VLC will do just fine):

sudo apt-get install gxine libxine1-ffmpeg

Now you can test a DVD with VLC, Kaffeine, Gxine or whatever your favourite media player is. Enable deinterlacing (VLC > Video > Deinterlacing > Blend) if playback is choppy or if you notice artifacts.

Note: Those of you still having DVD playback issues after installing the above packages should try the solutions in the troubleshooting section, which you can find at the end of this how-to.

PS : all credit goes to @reassuringlyoffensive

---

### Post by nifty542 on 2008-08-07
Hi, thanks all, been incredibly busy with work. Sorry for the late reply. Well, did all that was suggested/recommended. Still the same result. Dvd plays, but to a menu I haven't selected- cast commentary. If it helps at all, it works in Mepis, downloading the same packages (sorry, folks I know this is an issue- but thought it might tell you something)

Thanks, and kind regards

Nifty

---

### Post by mc4man on 2008-08-07
Try this
In upper panel right click on Applications -> edit menus. On left side highlight sound & video, on right side right click on vlc -> properties.
Change the launch command to this (copy and paste or make sure there is a space between vlc and %m)
```
vlc %m
```

---


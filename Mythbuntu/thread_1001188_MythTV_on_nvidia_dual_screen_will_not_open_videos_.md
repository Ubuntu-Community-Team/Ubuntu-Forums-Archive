---
title: "MythTV on nvidia dual screen will not open videos on TV"
date: 2008-12-03
forum: Mythbuntu
---

### Post by mwcrowley on 2008-12-03
I have nvidia dual screen spanning across my monitor and TV screen.  MythTV opens on the TV and I'm still able to use the monitor.  MythTv plays back recorded shows and watches TV on the TV.  However when I open up videos, they open on the monitor.  I have played around with mplayer command line flags but cannot get mythTV or mplayer by itself to open up the mplayer window on the TV.
I have searched and found one thread, but no solutions,
please help,
thanks.

---

### Post by fatmonk on 2008-12-04
TV and recordings are probably using the internal player, and videos mplayer.

mplayer is obviously using a different area of your desktop which coincides with your monitor rather than your TV.

I think the usual is to set up your system to use cloned screens on both monitors rather than a double-wide screen.

That way everything should open up on 'both' cloned screens.

There is a settings in nvidia-settings to clone the screens.

-FM

---

### Post by mwcrowley on 2008-12-05
Thanks for the reply but I don't want cloned screens,  I want to be able to use the desktop while mythtv is running or mplayer is playing.  
What I'm really asking for is the mplayer command lind flag that will tell mplayer to open on the tv.  
Also, I'm asking if I have to turn off twinview, forget about nvidia-settings and use xinerama instead.
Thanks.

---

### Post by mwcrowley on 2008-12-13
anyone else have a clue

---

### Post by bmwman on 2008-12-15
I have the same issue. Any updates on solution?

---

### Post by utar on 2008-12-15
Have you tried the "display" command line option.  To quote the mplayer help:

```

&#8722;display <name> (X11 only)
	

Specify the hostname and display number of the X server you want to display on.

EXAMPLE:
	

&#8722;display xtest.localdomain:0

```

I would try 0 and 1 and see if that works.

Edit: use "echo $DISPLAY" to find your display name

---

### Post by SteveGodfrey on 2008-12-15
Don't ask me why but I had to completely disable compiz to get Video playback in MythTV working.

---

### Post by newlinux on 2008-12-15
Use the display option or variable, or if the internal player is displaying recordings on the right monitor try switching mythvideo to using the "Internal" player.

Are you using just plain 2 displays for you TV or are you using xinerama to do 2 displays?

---

### Post by bmwman on 2008-12-15
I'm trying to use the TV as main screen. I don't caare if the laptop display anything because the lid would be closed anyway. Is there any command to make the mplayer to display on the TV? Everything else is showing fine.

---

### Post by zekemx on 2009-06-01
Ok Now.

I have an Nvidia Card with two outputs.

One is connected to my monitor and the second is to my HDTV.

My Monitor is Screen 0 while my TV is screen 1.

I am using Xinerama with 2 Xsevers,

In Mythtv I went to:

Utilities / Setup
Setup
Media Settings
Video Settings
Player Settings

In the Defaul Video Player I replaced:

mplayer -fs -zoom -quiet -vo xv %s

with:

mplayer -fs -zoom -quiet -vo xv %s -xineramascreen 1 %s

Now I am able to play videos in my HDTV as well as MythTV scree, and I can still use my monitor for other stuff, like using OpenOffice, etc.

Hope this helps..

---


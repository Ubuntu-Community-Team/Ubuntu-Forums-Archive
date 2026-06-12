---
title: "Is there a way to make MPlayer quit after done playing file(s)?"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by DasCrushinator on 2008-02-29
Just what the title states.

---

### Post by cozmicharlie on 2008-02-29
Love it when people actually put a good description in the title - much better than "Ubuntu sucks or Need help immediately".

Do you mean as a stand alone player or from the browser?

I will assume stand alone(this may work for the browser but I don't know):

Open mplayer>right click on it to open the menu>preferences>Misc and uncheck show video window when inactive.

See if that works for you.

---

### Post by DasCrushinator on 2008-02-29
> **cozmicharlie said:**
> Love it when people actually put a good description in the title - much better than "Ubuntu sucks or Need help immediately".

Do you mean as a stand alone player or from the browser?

I will assume stand alone(this may work for the browser but I don't know):

Open mplayer>right click on it to open the menu>preferences>Misc and uncheck show video window when inactive.

See if that works for you.

I agree, makes me not even want to click the thread.

Actually, I already have that unchecked, but maybe I should shed a little light on what I have done and what I am trying to accomplish.

I sometimes watch movies at night on my computer and would like gmplayer/mplayer to completely quit when done playing.  This is so the computer can let the monitor go to sleep.  In order to not have the computer go to sleep during playback, I followed this thread ([http://ubuntuforums.org/showthread.php?t=284804](http://ubuntuforums.org/showthread.php?t=284804)).  It works perfectly, except if I fall asleep while watching a video, it will keep the screen on all night (which obviously isn't good).

---

### Post by cozmicharlie on 2008-02-29
OK - I see what you are doing.  I could not find anything - I looked at various players (vlc smplayer) and I did not see any function to shut it down after play back which means you would have to either write a script or modify crazy-cows script.  Maybe if you post in that thread, someone can point you to a a solution.  Sorry I can't be of more help.

---

### Post by rvm4000 on 2008-02-29
SMPlayer doesn't have any option to shut down the computer after playing, but there's a modified version made by an user which does:
[http://smplayer.berlios.de/forums/viewtopic.php?pid=1107#p1107](http://smplayer.berlios.de/forums/viewtopic.php?pid=1107#p1107)

---

### Post by DasCrushinator on 2008-03-01
> **cozmicharlie said:**
> OK - I see what you are doing.  I could not find anything - I looked at various players (vlc smplayer) and I did not see any function to shut it down after play back which means you would have to either write a script or modify crazy-cows script.  Maybe if you post in that thread, someone can point you to a a solution.  Sorry I can't be of more help.

Not a problem.  Might end up doing just that.

> **rvm4000 said:**
> SMPlayer doesn't have any option to shut down the computer after playing, but there's a modified version made by an user which does:
[http://smplayer.berlios.de/forums/viewtopic.php?pid=1107#p1107](http://smplayer.berlios.de/forums/viewtopic.php?pid=1107#p1107)

Well, I am just wanting MPlayer to quit so the screen can fall asleep, not tell the PC to shutdown.

---

### Post by xcloud9x on 2008-03-01
If you start mplayer from the command line it will exit when the file is done.

---

### Post by DasCrushinator on 2008-03-02
> **xcloud9x said:**
> If you start mplayer from the command line it will exit when the file is done.

Only closes the video window for me. :(

---

### Post by rvm4000 on 2008-03-02
You're probably running gmplayer and not mplayer (mplayer only shows the video window, no controls).

mplayer completely closes when it finishes to play. 

Just open a console and type:
```

mplayer full_path_to_file_you_want_to_open

```

---

### Post by DasCrushinator on 2008-03-02
> **rvm4000 said:**
> You're probably running gmplayer and not mplayer (mplayer only shows the video window, no controls).

mplayer completely closes when it finishes to play. 

Just open a console and type:
```

mplayer full_path_to_file_you_want_to_open

```

Correct, I guess I should clarify and say that I want Gmplayer to quit.

---

### Post by rvm4000 on 2008-03-02
I don't know if that can be done with gmplayer, but smplayer can do it. There's the option "Close when finished" in preferences.

---

### Post by DasCrushinator on 2008-03-03
> **rvm4000 said:**
> I don't know if that can be done with gmplayer, but smplayer can do it. There's the option "Close when finished" in preferences.

I guess this will have to do.

Thanks to everyone in this thread!

---


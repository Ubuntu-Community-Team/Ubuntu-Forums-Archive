---
title: "qjackctl won's save settings"
date: 2007-10-29
forum: Multimedia Production
---

### Post by SteinbergerNate on 2007-10-29
Hello,
I just figured out some settings that work great for me in ubuntustudio on qjackctl. The only problem is that I can't get it to save the settings. I have to put my settings in every time I get into qjackctl. It won't let me change the name from (default) and even when I click save, exit and get back into qjackctl it has gone back to the default settings.

I checked .jackdrc and it looks like it's saved MY settings to that file but it doesn't load them or give me the option to load them.

Am I missing something here?

---

### Post by lukjad on 2008-06-27
Hi!
Just to start the ball rolling a few things that would be good to try. 
   1) Create a folder in your home directory and copy the .jackdrc file into it. Next delete the hidden folder. the start jackdrc again (after a reboot, just to be sure) and reput in your settings. If that works, great!
   2) Have you tried compiling it yourself? I know that it can be a pain but maybe it will work for you.
   3) Have you tried to do a fresh reinstall and/or install (with a fresh install) to a newer version? Sometimes it could just be a bug. If you feel up to it, backup everything on a few CDs or DVDs and pop in the new Hardy Heron Ubuntu Studio and give it a whirl. (I must warn you though that the whole Hardy platform seems to have DVD and movie clip playback issues. [See:[http://ohioloco.ubuntuforums.org/showthread.php?t=797937]](http://ohioloco.ubuntuforums.org/showthread.php?t=797937]) So this may not be the trick for you.)
Hope this helps. If it doesn't at least it may get someone more knowledgeable here.

---


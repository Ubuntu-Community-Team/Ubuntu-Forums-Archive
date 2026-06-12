---
title: "Cinelerra - choppy playback"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by Quicky on 2006-12-06
I’ve just installed Cinelerra and spent about 10 minutes playing with it but it seems that playback of video within the program is choppy.

If I load a DV file which has been imported from my Handycam by Kino and play it in Cinelerra, both the audio and video stutter considerably. This doesn’t occur when playing it in Kino.

Does anybody know if there are any settings within Cinelerra that I can adjust which would improve playback performance?

---

### Post by rudlavibizon on 2006-12-11
Same here. I also notice that the same  happens in Mainactor. 
Btw does anybody have openGL in cinelerra with an ati card?
I read that it should be compiled with openGL support and tried installing from svn source but it crashed during the make "operation" :confused: . If anyone knows how to install cinelerra with openGL please post a HOW-TO.

---

### Post by Quicky on 2006-12-12
I'm beginning to think that my computer simply isn’t powerful enough to run Cinelerra effectively. It’s only a laptop with an Intel integrated graphics card, so it would be easy to believe that this is the problem.

What’s annoying though, is that Kino (and its limited editing capabilities) runs flawlessly during playback, editing and rendering. It just doesn’t have quite the level of functionality that I’m interested in.

Why something as basic as video playback should differ so dramatically between the two programs is bizarre.

---

### Post by rudlavibizon on 2006-12-12
I run it on amd64 3000 with 1GB ram and radeon x1300 and it's still choppy. When i play video either from timeline or viewer the framerate oscillates from 23 to 27 fps (for PAL DV video). You can check this if you playback with preferences window opened. It seems odd that the framerate isn't fixed. This could be, though, that this is because Cinelerra is resolution and framerate independent and that might mean that it is more like After Effects (if you are familiar with Adobe programs) than Premiere. On the other hand After effects (if your computer is fast enough to reach it at all) doesn't go over the set project/composition  framerate. 
The other thing that annoys me is interlaced footage playback. Why do I have to see the fields? 

What i want to find out is does openGL fix these issues, if it does than things are not so hopeless for linux video editing. :-k

---

### Post by rudlavibizon on 2007-02-01
Well what do you know, i just found out that the playback isn't choppy on my box any more. Weird sh*t! I don't remember changing any settings but it happened in the last few days probably fixed by an update. So if you had similar problem checkout your favorite free (as in free speech) video editor again. :D

---

### Post by Ubuntiac on 2007-04-07
> **rudlavibizon said:**
> Well what do you know, i just found out that the playback isn't choppy on my box any more. Weird sh*t! I don't remember changing any settings but it happened in the last few days probably fixed by an update.
Where did you install it from?

I've got the Ubuntu repositories version installed and still get this problem...

Did you end up managing to install from the SVN source?

---

### Post by rudlavibizon on 2007-04-07
I installed from source and some debs (that was when i was on edgy, still haven't installed it on feisty) from different repos and the problem was the same until some update fixed it. Here are some links i followed ( if memory serves me well): 

from source: [http://ubuntuforums.org/showthread.php?t=320701&highlight=cinelerra+svn]("http://ubuntuforums.org/showthread.php?t=320701&highlight=cinelerra+svn")

from .deb packages: 
[http://ubuntuforums.org/showthread.php?t=294007&highlight=cinelerra]("http://ubuntuforums.org/showthread.php?t=294007&highlight=cinelerra")

You should probably check out cinelerra CVS website for latest information on installing it : [http://cvs.cinelerra.org/getting_cinelerra.php]("http://cvs.cinelerra.org/getting_cinelerra.php")

Also [Ubuntu Studio]("http://ubuntustudio.org") team had it compiled but it won't be included in the first release due to licensing issues. 

If you need a more straight forward editor try [Kdenlive]("http://kdenlive.sourceforge.net/index.php"), they have some debs for Ubuntu on their wiki. It lacks features compared to Cinelerra but is more efficient in terms of system resources.

---

### Post by organica on 2007-09-23
Try changing the settings in Cinelerra.

Settings>Preferences>Playback Tab>Audio Driver - Change to Alsa and check Stop playback locks up.

Fixed the choppy playback for me.

Using the CVN from the cinelerra community repo.

---

### Post by cotcot on 2007-09-23
Playback will be better with openGL  (select X11-OpenGL in Settings --> Preferences --> Playback   :  Video Driver.
Select ALSA for audio and if playback stalls within a couple of seconds thick "Stop playback lockups" in the same window as the video driver above.
Cinelerra asks more resources than the others (kino, kdenlive, ....). There is something in the manual explaining why. (something like rendering during playback).

I read that there are sometimes problems with compiling cinelerra with OpenGL.

---

### Post by daradib on 2007-09-24
> **organica said:**
> Try changing the settings in Cinelerra.
Settings>Preferences>Playback Tab>Audio Driver - Change to Alsa and check Stop playback locks up.
Fixed the choppy playback for me.
Using the CVN from the cinelerra community repo.

Fixed my problem as well. Thanks.
I'm using ATI Radeon (fglrx drivers) with this 64-bit repository
```
deb http://giss.tv/~vale/ubuntu64 ./
```

---


---
title: "mplayer spawning dozens of threads. How to prevent it?"
date: 2013-04-19
forum: Multimedia Software
---

### Post by mtdewd on 2013-04-19
I'm not even using mplayer, but several times per day, I notice the computer bogging down. Checking system monitor, I notice a dozen or more "mplayer" threads running. I kill them all, but they come back later. I use vlc to watch a movie now and then, but otherwise I'm not using any video software (that I know of.)

Oh, I do have a logitec usb webcam plugged in, and once or twice a week I run gtk uvc video recorder to record a short video at my desk, in case that is related?

I'm attaching a screen shot of system monitor to show the many mplayer threads.
[ATTACH=CONFIG]241551[/ATTACH]
Any ideas on how to stop mplayer from replicating like this and bogging down my computer?

---

### Post by stinkeye on 2013-04-19
In system monitor preferences, choose to show  the command line which may give you a hint as to what is actually running.

---

### Post by mtdewd on 2013-04-26
Thanks for the suggestion on system monitor. It looks like each instance was created by a screensaver called electricsheep, which I was running. I changed to one of the standard screensavers, and have not had the problem for several days now since I changed it. I guess the problem lies with that software.

---


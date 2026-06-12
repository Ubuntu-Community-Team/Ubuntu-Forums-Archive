---
title: "VLC player not opening"
date: 2009-04-13
forum: Multimedia Software
---

### Post by karthik_jce on 2009-04-13
Hi,


I had VLC media player installed on ubuntu 8.10 and it was working fine till two days back. But suddenly, today morning I find that VLC media player is not opening atall.

I tried to do right click on media files and Open with VLC player and also tried it directly from the applications menu, but it is not opening.

I tried to completely uninstall all the vlc packages through synamptic package manager, and reinstalled everything again. But still the same problem, VLC player is not opening.

Could anybody give some pointers for troubleshooting the problem?

Regards
Karthigeyan

---

### Post by Cybie257 on 2009-04-13
I had a short time (couple days) where I had a similar problem. Try going to Update Manager and seeing if there are any new "SYSTEM" updates ready to download and install. Sometimes that fixes such problems. It fixed mine. 

Good luck. VLC is a great media player.. Use it in Windows and Linux. :) 

-Cybie

---

### Post by 3rdalbum on 2009-04-13
Merely reinstalling software that crashes or doesn't open, will fix nothing at all. I'd be surprised if it does anything on Windows, actually.

Usually if a program crashes on opening, it's the result of a corrupted preferences file. Preferences files are held in a hidden file or hidden directory in your home directory, and VLC is no exception. If you enable "Show hidden files" in Nautilus (the file manager) you will see a folder called ".vlc" inside your home directory. Delete it and empty the trash, and you'll probably find that VLC will open again.

---

### Post by fdrake on 2009-04-13
post the output of the terminal with the commnad "vlc ~/Desktop/music_file.mp3"

---

### Post by mc4man on 2009-04-13
There's usually 2 reasons vlc won't start (other than not being installed

First as just mentioned the config is messed up 

Try this from the terminal
```
vlc --reset-config
```

The other is it's crashed but the process is still running. A reboot solves that or go to System -> administration -> system monitor -> processes and see if vlc is listed. If so, right click on -> kill process. Then restart with above command


(in vlc 0.9.x the config now is in home folder -> .config/vlc

---


---
title: "Teach a man how to change monitor res, drink WINE and manipulate X-server ?"
date: 2011-08-26
forum: Multimedia Software
---

### Post by deckoff on 2011-08-26
This is a multi-part question 
**What I want to do** - I want run a few old WINE games in a separate X-server window, changing the resolution on the way.
**What I got right**All games run ok, in a virtual desktops(provided by WINE). All are installed in their won wine prefix, I used PlayOnLinux to do that. Games, that run in resolution, lower than mine, will start in a window.
**Where I fail**

**1)** Running a game with
```
xinit /usr/share/playonlinux/playonlinux --run "Heroes3" -- :1 vt8
``` starts the game. **I have no sound though**. I read that executing```
ck-launch-session
``` should solve the problem. I dont know how to run it - no matter is I start from tty or Konsole I cannot input anything. Strangely, in every session I am logged in, I hear sound... tty1 and x0 will have sound, but x1 will not
**2)** Adding a new resolution  - I read all here. 800x600
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")
I added this successfully, but when I select the new resolution form the drop-down menu, Ubuntu will fall back to default 1024x768. So I want to have this lower resolution, to be able to start the game in the res it runs native.
**3)** xinit command that specifies the selected resolution will be bonus.. I think ```
xinit /usr/share/playonlinux/playonlinux --run "Heroes3" -geometry =800x600 -bpp 16 -- :1 vt8

``` should be the one I need, but since I cannot successfully change my res, I dont know if it right.
I run Kubuntu 11.04, but running the games in Ubuntu provides the same results. This is a thinkpad x40 laptop, IBM. the video is i915 , which is quite buggy and I am sure it causes at least half of the problems.

---


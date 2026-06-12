---
title: "Games freeze new computer running Gutsy"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by sdrawkcab on 2007-12-22
Yesterday I built a new computer. I put Gutsy Gibbon on the computer without a hitch. I have an 8500GT NVidia graphics card in it, so I wanted to try out some cool games. I downloaded Nexuiz, Sauerbraten, and Tremulous. They run fine for the most part. Until, all of a sudden my screen goes blank for a second, then it shows in a smaller window instead of fullscreen. At this point everything becomes unresponsive. I can't Alt+F10 or Alt+F4 the window. I can't move my mouse, and it seems the only thing I can do is restart. Although, I did get to a fullscreen command line on accident by bashing the keys some...It's been a little while since I've used Ubuntu so I couldn't remember how to exit.

Anyhow, I'm playing these games online with other people. I'm using the restricted driver for the graphics card at the moment. 

Thanks for any help.

---

### Post by tgalati4 on 2007-12-22
When you exit a game, the desktop resolution sometimes gets messed up.  It's a fact of life that there is poor handling between the game and the desktop/window manager.  

Your computer is not locked up.  If you can see the caps-lock light, then the system is still processing keyboard requests.

Control-Alt-Backspace will reset the xserver (but take down any programs you currently have running in it.).  On my system, I have to do it twice to get a working desktop after openarena.  With ppracer, the resolution is changed, but I can still move around to reset it.

Hitting alt-F5-F8 will take you to different text consoles.  You can use these to shutdown, but not reset the xserver since it's already running, just in an oddball configuration.

This behavior is consistent on Linux Mint 4 (gutsy-based) with an Intel i945gm chipset.

---

### Post by sdrawkcab on 2007-12-23
The thing is, I'm not exiting the game. It runs in a window. I can see the caps lock light, but nothing happens. It isn't triggered by any one thing, just after a while it decides to mess up.

---

### Post by mn123 on 2007-12-28
I was having the same problem until I turned off the screen saver. After that, I haven't had any issues. I hope this helps.

---

### Post by yellowdub on 2008-01-02
I was also having the same problem and found that dropping the desktop screen resolutiuon to 1024 x 768 also solved it!!
I will however try the screen saver option as the low resolution looks pants!!

---


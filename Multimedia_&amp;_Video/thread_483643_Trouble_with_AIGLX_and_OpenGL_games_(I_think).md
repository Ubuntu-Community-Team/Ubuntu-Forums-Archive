---
title: "Trouble with AIGLX and OpenGL games (I think)"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by 09amw on 2007-06-25
I have a Dell Latitude D610 notebook with the Intel integrated Mobile 915GM graphics chip.  I believe that AIGLX comes activated by default in my distribution of Ubuntu (Feisty), and I know that it is currently set up, because I'm running Compiz Fusion (quite nicely, if I might add).  However, I am unable to run the game, as it crashes my X server every time that I try to start it.

So, first, is there a documented history of conflicts between AIGLX and OpenGL games?  (Note: I can run the LXDoom port of Doom while AIGLX is enabled, but not while Compiz is running -- it's transparent for some reason when I try to run it with Compiz also running).  If there is such a documented history, how can I log into a session with AIGLX disabled?

If this is not the case, what information can I provide to help figure this out?  Tremulous (the game in question) seems like an awesome game, and I'd really love to run it. 

Thanks a lot for the help!

award

---

### Post by Cobra78 on 2007-06-30
Same problem: COmpiz Fusion runs, but deactivate direct rendering on my 950GMA, i'm also unable to paly videos -.-

---

### Post by 09amw on 2007-07-26
Ok, so I managed to deactivate AIGLX and tested again, to see if that was the problem.

It wasn't.  Every time I try to run a 3d full-screen game, my X server is restarted, and I am presented with the login screen again.  This does not happen when I run 2d full screen games, however.  Does anyone know a fix for this?  Or what the problem is?

Oh, I disabled AIGLX by adding the following lines to my xorg.conf: ```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

Thanks for the help.

Award

---


---
title: "[SOLVED] Two issues with fullscreen games on Gutsy"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Hazed on 2008-03-23
Whenever I run fullscreen games in Wine, they are never really fullscreen. I can still see the Ubuntu bar at the top, as shown in the below screenshot. I can click it and open things etc. This happens with all games I have tested, including World Of Warcraft, Half Life 2, Team Fortress 2 and Portal. Its especially annoying in World Of Warcraft as it cuts off the skill bar!

[[IMG]http://img225.imageshack.us/img225/5417/wownonfullscreenou7.th.png[/IMG]](http://img225.imageshack.us/my.php?image=wownonfullscreenou7.png)

Is there anyway to fix this?

Another issue I am experiencing is World Of Warcraft specific. Besides from the fact I can't change the video settings (it crashes with an error message and closes when I try to change any video settings, which means I can't run it in window mode =[ anyone who has a solution to this please let me know, I have tried gxWindow "0" in the config.wtf to no avail). Whenever I do click outside the window and then go back to the game, all the character models disappear (see below)...

[[IMG]http://img135.imageshack.us/img135/9427/wowtheybegonejw6.th.png[/IMG]](http://img135.imageshack.us/my.php?image=wowtheybegonejw6.png)

Any help on these issues is greatly appreciated.

I am running Ubuntu Gutsy Gibbon on a Dell Vostro 1500. 2GHz Dual Core Processor, 3GB DDR2 Ram and an NVidia GeForce 8600 GT M.

Cheers

---

### Post by Hazed on 2008-03-23
Ok I kinda fixed the first issue by disabling the option in Wine's config that lets the window manager manage emulated applications, but that now means that when I am running a game in fullscreen mode, I can no longer use any of my other 3 virtual desktops, or alt-tab out of it... Any other solutions?

Issue #2 is still not fixed with this approach

---

### Post by Hazed on 2008-03-23
Triple post, sorry.

But running it using Wine's Virtual Desktop option is the perfect solution to all of my problems. And I can continue using Alt-Tab, Windows-Tab and the cube without any issues.

Woohooo! Solved!

---


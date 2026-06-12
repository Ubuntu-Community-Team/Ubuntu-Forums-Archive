---
title: "Streamtuner live365 empty?"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by PurplePenguin on 2007-01-03
I'm enjoying Streamtuner right now... I used to have about ten streams bookmarked in a different program, but it's so nice to be able to search and have such a big selection of stations to pick from.

My question is this:  Live365 doesn't seem to work for me in Streamtuner.  I click on the Live365 tab, select Editor's Picks or Search, and can see that it's loading something in the status bar at the bottom of my browser.  The thing is, it's not displaying anything on the screen.  No stations to pick from at all. :(

Is this a new problem with Streamtuner?  Does anybody have any idea if I might be doing something wrong?  I even tried putting my live365 username and password in, but nothing helps.

---

### Post by Gotou on 2007-01-06
Same here.  It's been that way for awhile.  Streamtuner Live365 has disappeared in both Dapper and Edgy.  So far no luck Googling for an answer.

---

### Post by PurplePenguin on 2007-01-06
I guess it is sort of comforting knowing that I'm not the only one with the problem! :)  Thanks for the reply!  Hopefully some kind of workaround will appear sooner or later.

---

### Post by Gotou on 2007-01-06
After an hour of Googling I found a few pieces to put together.
There is a patch but I couldn't get it to work.
Below is a list of what I did.  Hopefully someone can find what I did wrong, let us know to fix it and we all can have Live365 back in StreamTuner again.

1. Uninstalled StreamTuner through Synaptic.
2. Rebooted the computer (just to be thorough).
3. Extracted streamtuner-0.99.99.tar.gz file.
4. Went online to this web url ->   [http://download.savannah.gnu.org/releases/streamtuner/streamtuner-0.99.99-live365.diff](http://download.savannah.gnu.org/releases/streamtuner/streamtuner-0.99.99-live365.diff)
5. Copy/pasted text from the web url into a text editor.
6. Saved the file as live365.diff in the extracted streamtuner-0.99.99 directory
7. Started a terminal.
8. CD'd into the streamtuner-0.99.99 directory.
9. Used this patch command -> patch -p0 <live365.diff
10. Then started to compile the program -> ./configure
11. Once configure was done -> make
12. Once make was done -> sudo make install
13. Rebooted the computer (again, just to be thorough)..
14. Started a terminal.
15. Typed in -> streamtuner.
16. Tried reloading the Live365 category and still came up empty.
17. Uninstalled streamtuner -> sudo make uninstall.
18. Rebooted the computer.
19. Reinstalled StreamTuner through Synaptic with the hopes that someday a fix will make it's way through Synaptic.

Luckily I don't have a subscription to Live365.  I guess I will be exploring the other broadcast streams in StreamTuner more often now.

---

### Post by haiku99 on 2007-01-06
I have the same problem and found that streamtuner's  page says that this is a known issue caused by changes to Live365's site and is being worked on....about 2/3's down this page

[http://www.nongnu.org/streamtuner/](http://www.nongnu.org/streamtuner/)

---

### Post by tv0571 on 2007-01-08
I too have come to the conclusion that 365 won't work with Streamtuner.

But I can't get my Firefox to load any Live365 streams either.  Firefox (1.5.0.9) starts to load the stream in a window, gets half way through the window painting and then crashes hard.  Force Quit is the only option.  

Live365's instructions here: [http://wiki.live365.com/pmwiki.php?n=Listening.Linux](http://wiki.live365.com/pmwiki.php?n=Listening.Linux) don't work for me.

Can anybody in UbuntuLand use Live365?

---


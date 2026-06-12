---
title: "Mythgame - Can I add &quot;wine&quot; games or native Linux games and how?"
date: 2008-09-11
forum: Mythbuntu
---

### Post by bmwman on 2008-09-11
I've been searching around since I got my Mythgame to work with MAME. I found some info how to add Linux games in there as well but i couldn't really get it to work. Someplace I read that I need to create links and put in the roms folder but that didn't work. I tried creating a new Linux player and pointed it to the Supertux game but that doesnt work either. It would try to start but nothing happens. 

I was wondering if somebody knows exactly how to add and make the other games work. Also is it possible to add games which are installed with Wine or Crossover office7?

Thanks.

---

### Post by dsbw on 2008-09-14
Have you checked this [link]("http://www.mythtv.org/wiki/index.php/MythGame")? 

I think there are some emulators that work out of the box, but for games that aren't in the set of known emulators, you'll need to manually create scripts and put images in, etc.

---

### Post by bmwman on 2008-09-15
I do have MAME working but was wondering if I can get PC games like Heroes 5 or Need for speed in there. Or at least Linux games that I have under Applications - Games.

---

### Post by dsbw on 2008-09-15
Did you try this (from the link):

 PC-Game Setup

To Setup PC Games Create a Directory with Scripts which run your different PC Games. (for example: /usr/games/scripts). You also can link the game executable to this directory if you don't want to create a script.

Then you have to create a game-player which runs your scripts.

Player Name: PC-GAMES 
Type: Other
Command: %s
Rom Path: /usr/games/scripts

?

---


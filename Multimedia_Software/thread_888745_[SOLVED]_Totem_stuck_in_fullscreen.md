---
title: "[SOLVED] Totem stuck in fullscreen"
date: 2008-08-13
forum: Multimedia Software
---

### Post by M4rotku on 2008-08-13
Hey all, 

I have a problem that's probably easy to solve but I can't seem to do it.

I have been using Totem for a long time now, so I know all of the controls and it's not a noob problem.  (hopefully saying that won't come back to bite med. :)

I put totem in fullscreen to watch a movie and then I clicked the 
view -> show controls option so that I could tell how much time is left.

Now, it's stuck in fullscreen.  I can still show/hide the controls, and the exit full screen option is available, but when I click it, it doesn't do anything.

I have tried reinstalling totem and the config files stayed.  I want to try to avoid purging totem b/c that would remove a lot of other programs.  If it helps to know, I'm using the xine engine.

How can I fix this?

Much thanks,
M4rotku

---

### Post by mc4man on 2008-08-13
Go into your home dir. -> .config and open the totem folder. Inside are 2 files, look in the state.ini and try to adjust. Otherwise just delete it  or the totem folder itself.

---

### Post by M4rotku on 2008-08-13
Thanks, that worked great.

---

### Post by LoSt180 on 2008-08-24
awesome, I was having the exact same problem. Deleted state.ini file, all good now. 

only difference: in gutsy the file was located in .gnome2/Totem (I'll upgrade my media center eventually)

---

### Post by ReyJames on 2008-10-26
Helped me out of the same problem - thanks

---


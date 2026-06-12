---
title: "MythTV losing it's &quot;watch TV&quot; option"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Yoooder on 2007-01-18
I'm new to MythTV, and I might just be doing something wrong or have a misconception.

After my first scheduled recording completed the "Watch TV" menu item disappeared and has not been seen since.  I have checked that the Tuner is not currently in use--it's not recording anything, and I have future scheduled recordings (would this have anything to do with it?).

Any info would be wonderful!  Thanks!

---

### Post by edward4130 on 2007-01-18
I have yet to have this issue but it would not hurt to restart the Mythtv backend

sudo mythtv-backend restart

I wonder if it is a mysql thing not releasing the recording and acting like the card is in use.  This *could* take care of it.  

Also if the future scheduled recording was happening soon it could close you off from the card.  question... Can you play your recording?

-Edward

---

### Post by Yoooder on 2007-01-18
edward4130: I've tried restarting the backend, as well as the machine to no avail.

I *think* it may have moved the menu item from the first screen to within a sub-menu.  I was in MythTV very briefly over my lunch break and think in hindsight I think I might have seen Watch-TV.

I'll post whether or not this is the case once I can get home and find out for sure.

---

### Post by Yoooder on 2007-01-19
"Watch TV" is back.  I had found a (differently named) sub-menu item that let me watch TV, and then after running back through MythTV's setup "Watch TV" popped back to the main menu as it had been.  Apparently there's a checkbox that I changed inside Setup that moved it around on me.

Thanks!

---


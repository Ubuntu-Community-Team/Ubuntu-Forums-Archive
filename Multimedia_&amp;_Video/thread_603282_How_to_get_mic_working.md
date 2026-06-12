---
title: "How to get mic working"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Caz'ar Xiladys'varion on 2007-11-05
I need to get a working mic working in linux or else it's back to windows....and I *really* don't wanna go there =P

It's a simple mic that plugs in directly into the microphone jack. I'm not sure how to get it working though. Any help?

---

### Post by Caz'ar Xiladys'varion on 2007-11-05
anyone there? no one's even looked at me post yet..

---

### Post by Phosphoric on 2007-11-05
I battled long and hard with my sound problems (still am).

A quick and easy fix for me, though not ideal, was to chuck out my nice Turtle Beach Santa Cruz sound card and stick in a crappy SB16 card.

Now Skype works, sound recorder works, Audacity works and even Kino video capture now works.

Somebody else will come along with reams of terminal work or fiddling with Alsamixer and maybe it will work for you.

---

### Post by Gremlinzzz on 2007-11-05
open your sound recorder///click file// choose open volume control///click edit then preferences .check every box .now you have access to the controls unmute everything and make sure to slide everything to full.in options tab i choose front mike.GL

---

### Post by Caz'ar Xiladys'varion on 2007-11-06
I get this when I try and open sound recorder.

Your audio capture settings are invalid. Please correct them in the multimedia settings.

When I go to Preferences -> Sounds and click test on audio capture I get this:

gconfaudiosrc ! audio convert ! audio resample !
gconfaudiosink profile-chatL resource busy or not available

---

### Post by Caz'ar Xiladys'varion on 2007-11-06
hm..now I can open it for whatever reason. umuted everything and still doens't work though.

Anyone have any ideas?

---

### Post by Caz'ar Xiladys'varion on 2007-11-06
c'mon guys...I'll have to go back to windows if I can't get this stuff to work.

Any help here?

---

### Post by Caz'ar Xiladys'varion on 2007-11-06
*bump*

---

### Post by Phosphoric on 2007-11-06
> **Phosphoric said:**
> I battled long and hard with my sound problems (still am).

A quick and easy fix for me, though not ideal, was to chuck out my nice Turtle Beach Santa Cruz sound card and stick in a crappy SB16 card.

Now Skype works, sound recorder works, Audacity works and even Kino video capture now works.

Somebody else will come along with reams of terminal work or fiddling with Alsamixer and maybe it will work for you.

Maybe?

---

### Post by Caz'ar Xiladys'varion on 2007-11-07
so the only solution to get mics working in linux is to buy this sound card? There's absolutely nothing I can do to get my existing mic working?

---

### Post by Caz'ar Xiladys'varion on 2007-11-07
c'mon...I spent good money on my sound card. I don't wanna go buy some ancient one. This is the last thing keeping me from moving from windows to linux...I need to be able to use my voice comms. Can't any of the linux experts on this forum setup a mic?

---

### Post by csat on 2007-11-07
This link has a possible solution that worked for me.

[http://geekybits.blogspot.com/2007/06/microphones-skype-on-ubuntu.html](http://geekybits.blogspot.com/2007/06/microphones-skype-on-ubuntu.html)

Good luck.

Csat

---

### Post by Gouz on 2007-11-21
Try in terminal

alsamixer 

then find the mic and using the arrows race the volume

---


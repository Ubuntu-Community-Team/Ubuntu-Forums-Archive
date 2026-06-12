---
title: "No Sound with fuhquake, choppy sound with ezQuake"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by jimbob1977 on 2007-05-16
Help! I've installed Fiesty Ubuntu - and the system all appears to work fine - sounds play fine.

Yesterday I installed quake 1 - and I can't get sound to work properly at all!

fuhquake tells me that the sound failed as its loading, and ezQuake plays very choppy echoing sounds that cause it to slow right down! Anyone got any ideas on how to fix this one?

Thanx - Jamie

---

### Post by fearpi on 2007-05-20
In ezquake:

s_khz 48
s_restart

Or, start it with the option:

./ezquake +set s_khz 48

This is the only frequency setting that gives me undistorted sound, however, there is a delay between an event and its sound. Let me know how you fare.

---

### Post by homerhomer on 2007-09-06
Fixed it on mine

just boot into ezquake,

Then go to Options, once in options go main tab on top and you'll see an option for advanced options, select it

Once you have done that change the sound hertz from 11 to 22

Then go to the config tab and select save

hope this works

---


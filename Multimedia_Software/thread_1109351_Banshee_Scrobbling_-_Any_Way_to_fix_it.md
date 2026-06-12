---
title: "Banshee Scrobbling - Any Way to fix it?"
date: 2009-03-28
forum: Multimedia Software
---

### Post by joey-elijah on 2009-03-28
I love using Rhythmbox, but Banshee is very pretty too. 

One thing that really annoys me about banshee is scrobbling - firstly it doesn't scrobble every track played and secondly you have to listen to 100% of the track for it to scrobble!  >,<

Rhyhtmbox uses 50% played to scrobble, which is what i also use in the official client set up with iTunes in Windows 7. 

I prefer 50% because sometimes you just need to hit 'next!' (overly long outro's etc). Whilst i appreicate this is a small issue, for many users last.fm is very important and having scrobbles missed because we can't adjust the setting annoys me!!

Is there anyway to change the amount played before it's scrobbles? (the defaults in the last fm client are 50% 75% and 100% respectively, maybe banshee should either intriduce a selection or just default to 50% like ryhthmbox.

edit: i'm running banshee 1.4.3

---

### Post by Rian46 on 2009-04-23
Yeah it's the same for me, half of my songs don't scrobble or appear in the now playing section on last.fm, pretty annoying! And I love banshee so it'd be great to have a fix for this tiny problem.

---

### Post by joey-elijah on 2009-08-28
The Last.fm plugin in banshee is still the same. 

Anyone know a) how to get Banshee to scrobble using the official client or, heck, even via the terminal!? 

failing that i suppose i'll have to tweak/create a plugin

---

### Post by joey-elijah on 2009-09-02
FYI

i downloaded a new version (2.0) of the plugin from git and it works flawlessly.

---

### Post by Anon Customer on 2009-12-22
I think scrobbling stopped for me after I upgraded, I was able to fix it by re-authorizing Banshee. The first thing to check if scrobbling stops is that you are still authorized and can connect:

In my version, Banshee 1.6 Beta 3 (1.5.2), this is possible by right clicking and selected Connect on the Last.fm icon in the left pane. If it can't connect then select Preferences try reauthorizing and then testing your authorization. 

My authorization test never resolved but after restarting Banshee scrobbling was working in real-time (Last.fm) knew it was Banshee sending the data and what I was currently listening to.

---


---
title: "How to stop Motion from Terminal."
date: 2009-03-25
forum: Multimedia Software
---

### Post by dchurch24 on 2009-03-25
Hi all,

I have a MythTV frontend running on Xubuntu in my living room. 

Recently I've being playing with pics controllers and ADU units and can control the lights in four of my rooms by adding menus to Myth to turn them on and off.

All of that is working fine (I just need to work out how to dim the lights when Myth starts playing a movie and I'm all set).

However, I also have a camera (USB) connected to the frontend machine which is being monitored using 'Motion'. 

This machine isn't particularly powerful, but is good enough to run Myth smoothly. I have Motion set up to email me with a snapshot when it detects motion, but when it does so, the TV slows down noticably. 

This isn't a problem usually, as I'd only want it recording motion when I am not at home.

What I'm trying to do is have two menus in Myth - one that starts Motion up, and one that stops it.

I have the menus setup and can start Motion in the background with no problem, I just can't workout how to stop it.

I have tried "killall motion" but that doesn't work. I can kill the process by 'sudo kill -9 [motion pid]' but then of course I have to put the password in and this also doesn't run from the myth menu.

Is there some way in which I can write a script to kill motion or bring it down gracefully?

Sorry for the verbosity.

---


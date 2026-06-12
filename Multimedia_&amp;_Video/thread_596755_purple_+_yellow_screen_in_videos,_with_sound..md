---
title: "purple + yellow screen in videos, with sound."
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by asbani on 2007-10-29
II'm having this odd problem, never happened to me before. and now it happened to me in gutsy 7.10 ubuntu for the third time, It's weird. I can't even disribe it but I will try.

After watching few videos, on any type, they work perfectly after awhile the same exact videos or same type even, Will not work anymore. they go purple/yellow screen, but the sound will still work. and when this problem starts, All and every kind of Video will be like that in every player, I mean if this problem starts. I try using VLC or mplayer or Totem, all of them will be having that same exact SCREEN, but with Sound working good. 

Restarting X will solve the problem. anybody experienced it before? Why this happening, and how to solve it. I don't want to restart X everytime, it shouldnt happen this way. here's a SCREENSHOT to give you a good example of how am I looking to video files right now.

[IMG]http://shell.lomag.net/~org/Screenshot-3.png[/IMG]

---

### Post by sublimespot on 2007-10-30
I have the same problem.

---

### Post by asbani on 2007-10-30
I found out another solution of this problem. It might be caused only when wine is up & running.


so you can just do

# wineserver -k

That'll kill every application that is running via wine. then video will work as normal. so that'll make me think it's a wine problem, nothing else (Maybe) I then updated my wine, from version 0.9.46 to 0.9.48 (The latest) and until now I didn't experience that same problem, 


Now this post to help those of you who are having the same problem as mine :D Cheers.

-asbani.

---

### Post by kaston on 2007-12-27
i don't think this is a wine problem.  i'm pretty sure i don't have wine installed and i still get it sometimes

---

### Post by kaston on 2008-01-01
anyone found a solution to this yet?  it seems to be happening more and more to me

---

### Post by eyyYo on 2008-01-07
I have the same problem, a restart takes care of it. Also if you can change video module in your player, change to something else. On VLC i use X11 as videomodule (crappy picture altough), When i tried asbani's fix, it worked too.

---


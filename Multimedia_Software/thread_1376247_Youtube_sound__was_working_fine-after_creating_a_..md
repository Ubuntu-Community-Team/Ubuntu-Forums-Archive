---
title: "Youtube sound  was working fine-after creating a .openalrc file it now doesn't work"
date: 2010-01-08
forum: Multimedia Software
---

### Post by ColeNi on 2010-01-08
I have a youtube sound issue. I just installed ubuntu 9.10 a couple of days ago. I had sound working perfectly fine except for two issues. the first was a kind of high-pitched whine that sounded in my headphone only when I wasn't playing any other sound, and the second was that the sound for the game Chromium did not work. 

While trying fix the game sound, I added or changed (I'm now not sure which) the  **.openalrc **file in the HOME directory, after which sound in youtube no longer works (and sound still didn't work in the game). Sound still seems to work on everything else including rhythm box, vlc, and system sounds, but no youtube sound.
I tried deleting the file I made, as well as having a file called .openalrc with either:

     Code:
     (define alsa-device "default")
(define devices '(alsa native)) 

or

     Code:
     (define devices '(native)) 

code inside of it. I'm very new to Ubuntu, so please make instructions simple.

Anyone else have this problem, any ideas?


EDIT: Nevermind, I swear I had already checked this but...the problem was just that firefox was muted.

---


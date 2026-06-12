---
title: "no sound in Amarok :("
date: 2008-05-01
forum: Multimedia Software
---

### Post by windoze87 on 2008-05-01
If i posted this in the wrong area, my apologies. Right now i'm trying to figure out a bit of a problem- I downloaded the Amarok media player today, and i have zero sound. I do have sound, though, on startup and when i use Rhythmbox and Totem Movie Player... libxine-extracodecs was installed when i downloaded Amarok, though, and the program shows it's playing music, but i don't hear anything... so i have no idea why i can't get it to spit any music out. I'm using the Xine engine with Amarok right now... I have a Realtek AC'97 audio card and i'm running Ubuntu 7.04. If anyone has any suggestions for me i'd greatly appreciate it!

---

### Post by mc4man on 2008-05-01
try going into settings->configure->engine and manually choose an output plugin

---

### Post by windoze87 on 2008-05-01
Beautiful. I changed it to ALSA and it worked perfectly... just when i think i'm getting the hang of Ubuntu, i learn something else lol thank you very much

---

### Post by windoze87 on 2008-05-01
welp, maybe i spoke a little too soon. I rebooted to go and wipe my Windows partition so i could have that hard disk to use in Ubuntu... well, i log back in and behold, Amarok doesnt play music again. It's highly confusing... the engine's still set to alsa, and everything. New suggestions, anyone?

---

### Post by redbob on 2008-05-01
It's usual when Amarok loses sound, that something else catches off sound control. Did you identified another program that is playing music simultaneous to Amarok (like Virtualbox, per example)?

---

### Post by windoze87 on 2008-05-03
nope, i didnt have any other multimedia programs open... i had Rhythmbox open PRIOR to opening Amarok, but i quit Rhythmbox before i opened Amarok.

---


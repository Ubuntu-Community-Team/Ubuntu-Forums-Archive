---
title: "Impossible to regulate audio volume and mic if logged in as root"
date: 2010-10-12
forum: Multimedia Software
---

### Post by N3tMast3r on 2010-10-12
Hi everyone,

As the title states, I am unable to regulate the audio volume if Iog in as root.
I have never had this problem before but after updating my two laptops to Ubuntu 10.10 final (32 bit on a laptop and 64bit on the other one) this problem started for both computers.
I looked for a solution on line and I found a guy who said to go to Users & Groups and set the "audio" for all the users who use the computer. Unfortunately, I am not able to do so because Users & Groups doesn't open if I am logged in as root. On the other hand it opens up if I am logged in as an other user but I am not be able to see the user "root".
The audio panel works fine if I log in with any user but root.

I would appreciate any suggestion.

Regards,

Andrea

PS. If I log in as root and type alsamixer in the terminal I can regulate the audio, and it actually works, but I would like to solve this problem without using every time the terminal to regulate the audio.

---

### Post by mikewhatever on 2010-10-12
So don't login as root. Simple.

---

### Post by N3tMast3r on 2010-10-12
wow thank you! I didn't think about it! -.-

By the way, I have Ubuntu 10.10 final 64bit on both my laptops.

---

### Post by N3tMast3r on 2010-10-17
Lonleeeey... I'm Mr. Lonley...

---

### Post by N3tMast3r on 2010-11-18
So, since the only thing people can say to solve this problem is "do not log in as root" (how dumb),
I decided to give the solution for people who might really need to login as root and use the audio without opening the terminal and type alsamixer every time!

Just add this at the startup:
 /usr/bin/pulseaudio

byeeeeeee

---


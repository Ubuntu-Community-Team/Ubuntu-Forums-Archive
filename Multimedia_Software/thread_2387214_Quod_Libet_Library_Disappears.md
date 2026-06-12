---
title: "Quod Libet Library Disappears"
date: 2018-03-16
forum: Multimedia Software
---

### Post by deanr2 on 2018-03-16
Hi.

Quod Libet is the only media player I've found that doesn't crash, freeze instantly or take hours to load my +500 gb music collection (although it does still stall when typing a search!).

The main issue I'm having though is that after shutting the PC down, the library empties itself and I have to re-scan everything again from scratch - which is clearly pretty useless as a music library. 

So the question is: How can I get it to retain the library from one day to the next?

Any help appreciated,

D.

---

### Post by mc4man on 2018-03-16
From what I see here if the added media is on another volume or an external drive then the default setting of "scan library on start" fails to scan that or those locations.
(- why makes no sense, seems a bug
So maybe try adding all then disable that option (if in fact your media is not on the volume Quod Libet is running on.
If that works you can always rescan, (manual), when wanting to add additional..

---

### Post by deanr2 on 2018-03-17
Thanks for the response. I've tried everything to no avail. Quod Libet is just a waste of space on my hard drive which has led to me starting another thread on the frustrations of trying to get anything to work on Ubuntu :-/

---

### Post by deanr2 on 2018-03-17
Update: Foobar 2000 installed via Wine, looking good, working well and retaining library!

---

### Post by deanr2 on 2018-03-18
Grrr. Foobar doesn't store my music library from one day to the next either. I'm really at a complete loss what to do other than switch back to WIN10 :-/

---

### Post by pvanryn on 2018-03-19
Have you tried Music Player Daemon? It takes a little more effort to set up, but it is worth it. There are a lot of different front ends for it.

It plays every format, updates quickly, very flexible, allows for streaming.

Good instructions [here]("https://help.ubuntu.com/community/MPD").

---

### Post by deanr2 on 2018-03-21
Thanks, pvanryn - maybe I'll check it out. I've always got on eye on the perfect audio player :D

Perhaps useful for other users on here I've solved the problem.

The problem was with the hard drive not mounting on boot - so QL couldn't load the library on start up. As mounting an external hard drive on start-up seemed to require (for me) complicated commands in the terminal, I uninstalled Xubuntu and installed Ubuntu Unity instead. Using the GUI it was an easy fix to go from: [FONT=Arial]disks > select hard drive > additional partition options > edit mount options > Automatic mount options [OFF-[/FONT][COLOR=#000000][FONT=Arial]ON[/FONT][/COLOR][FONT=Arial]]. 

As I said, problem solved and QL is holding up fine and is coping very well the 8000+ albums I've got. I'm surprised it's so smooth and unglitchy tbh and the search option works wonderfully quickly too!


[/FONT]

---


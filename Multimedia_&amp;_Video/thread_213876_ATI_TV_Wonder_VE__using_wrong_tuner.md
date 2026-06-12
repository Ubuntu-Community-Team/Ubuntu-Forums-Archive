---
title: "ATI TV Wonder VE  using wrong tuner"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by stratotak on 2006-07-11
Have a ATI TV WonderVE card and the picture is messed up..Now I  Know what the problem is and how to fix it..,well sort of.I knew how to fix it when I was running Slackware 9.1..The problem is the bt878 modules assigns it the wrong tuner type...it is assigning i t to use the PAL tuner not the NTSC tuner ..and the picture is all out of tune..The way I would fix it in Slackware was to pass on a option in modprobe config  to use tuner=17..it was something like alisas bt878 tuner=17..  Cant remember it exactly..its been along time since I have ran Slackware...But that always fixed it..Anyone know how to do this under Ubuntu??I could just go in and adjust every channel and fine tune it till reception is clear but I donr want to spend all that time adjusting all the channels..

---

### Post by bgood4000 on 2006-07-12
The correct option is "tuner=2" for NTSC Phillips tuner.

---

### Post by scxtt on 2006-07-12
i have that exact card and don't have to do anything out of the ordinary to get it working just fine w/ TVtime ...

---

### Post by stratotak on 2006-07-12
ok..well maybe your TV wonder VE uses a different chip or something.mines about  4 years old...but Ive always had that problem..Slackware,Fedora,Mandrake.....Like I said I kinda know what I need to do to fix it but not sure how to do it..I aded a modprobe.conf to /etc/ and added  options there..
 alias char-major-81 bttv
options bttv card=1 autoload=0 radio=0
post-install bttv insmod tuner type=2

But it didnt work..I just need to know what file needs to be edited ..Last time I had card in pc  distros were still using 2.4 kernel and it was different..2.6 changes things around and Im not sure exactly how its done..

---

### Post by scxtt on 2006-07-12
mines about that old too ...

but i think ubuntu uses /etc/modprobe.d/* and /etc/modules instead of modprobe.conf ...

---

### Post by stratotak on 2006-07-12
oh..well screw it..lol...I only watch a few channels anyway..sci-fi channel and about a half other dozen ones..ill just fine tune the 12 or so channels and call it a day..lol.. not goinmg to set here and fine tune 80 or so channels..lol..to lazy..

---


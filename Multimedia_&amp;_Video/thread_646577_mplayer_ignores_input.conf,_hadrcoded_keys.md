---
title: "mplayer ignores input.conf, hadrcoded keys? :/"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by citizenr on 2007-12-21
I removed /etc/mplayer/input.conf

my ~/.mplayer/input.conf :

MOUSE_BTN0 vo_fullscreen
MOUSE_BTN1 pause
MOUSE_BTN2 pause
MOUSE_BTN3 pause
MOUSE_BTN4 pause
MOUSE_BTN5 pause
MOUSE_BTN6 pause

but mplayer still thinks it knows better. For example when i press MOUSE_BTN6 it pauses, but when i let that key go it keeps on playing :/ It treats mousewheel (3 and 4) and side buttons (5 and 6) like that. Another thing is LEFT RIGHT buttons, i dont have binds for them but it thinks i want to seek with them :/

Is ubuntu mplayer build broken/dumped down by design?

---

### Post by Dimitriid on 2007-12-23
Same problem on Arch, I think its an error on mplayer.

---

### Post by citizenr on 2007-12-23
ok, now i know that double mouse on scroll wheel is standard SDL behaviour, SDL sends 2 events, press and release, and mplayer  is too stupid to recognize, its supposedly fixed in latest pre build

but i have no idea where LEFT RIGHT hardcoded binginds come from :(

---


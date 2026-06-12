---
title: "XMLTV on 10.04"
date: 2010-07-28
forum: Mythbuntu
---

### Post by axelsvag on 2010-07-28
After been stucked to 8.04 for a time I made a fresh install of the 10.04. When I tried the xmltv configuration in the backend I realized it was very difficult to say yes and no to the grabbers since the line was below the visible window not like a terminal window that just follows the last written line. Have anyone else experienced that or am I doing something wrong. By the way is there any way to update the xmltv package since there seems to be a newer one out there?

---

### Post by ian dobson on 2010-07-28
Hi,

Maybe just go to a terminal window, su to the mythtv user then run the grabber you want to use with the --configure? option.

If you want to install a newer version of the xmltv grabbers, uninstall the mythbuntu version then manually install the newer version. You might have to update other packages (perl libs etc), but your on your own.

Regards
Ian Dobson

---

### Post by axelsvag on 2010-07-28
It was just that " your are on your own " that scared me. I would have hoped for a ppa xmltv or something like that. Or is the autobuild the answer?

---

### Post by ian dobson on 2010-07-28
> **axelsvag said:**
> It was just that " your are on your own " that scared me. I would have hoped for a ppa xmltv or something like that. Or is the autobuild the answer?

Maybe there is a ppa for xmltv, but I've never come across one during my search for an updated grabber. In the end I wrote my own grabber.

Regards
Ian Dobson

---

### Post by axelsvag on 2010-07-29
OK I am impressed. So maybe you have some advice how I put a new grabber in mythtv and make it work in the mythbackend configure.

---

### Post by dibuntux on 2010-07-29
Yes, it is like that; with patience you can scroll the line reply yes or no to every channel question. I did it many times, it is a pain but in the end it works.

Hope it helps.

PS: Ian, you wrote your own grabber... your're the man!

---

### Post by axelsvag on 2010-07-29
It is really a pain to first have to enable mouse pointer then approve one line and use the mouse and then approve a new line. And for me 95% of the lines are uninteresting and the default is yes so I have to put in " no" on maybe 100+ lines. Maybe that is something for a "mythbuntu 100 paper cuts project" I am sorry I am too bad at writing code or else I could have been helping out this annoyance.

---


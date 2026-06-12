---
title: "Mythbuntu Diskless Applying timezone twice"
date: 2010-04-03
forum: Mythbuntu
---

### Post by Macus on 2010-04-03
Hi all

I just upgraded my mythbuntu back/front-end to 9.10 (as i needed to 'update my database schema')
thats all sorted and i just regenerated my disk-less image with:
 sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials=..

added things i need, all works fine except one thing
the time on my disk-less frontend is always wrong
it seems to be adding the gmt +10(i live in aust) twice

like its 8:30pm (20:30) 3/April  (the correct time)
but it changes it to 6:30 am 4/April

its never done this before and only started today when i updated

normally i would not care, but its preventing mythfrontend from starting

any idears?
thanks.

---

### Post by Macus on 2010-04-03
Ok,  think i found it

was not perfect as it was still off with daylight savings (wich ends today anyway) 

it was the ile /etc/defalut/rcS  chnage the line utc=yes to utc=no

I guess that is asking 'is the bios time utc?' which its not

---


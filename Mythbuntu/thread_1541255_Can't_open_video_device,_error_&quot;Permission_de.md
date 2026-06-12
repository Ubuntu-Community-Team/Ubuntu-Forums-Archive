---
title: "Can't open video device, error &quot;Permission denied&quot;"
date: 2010-07-28
forum: Mythbuntu
---

### Post by dardack on 2010-07-28
Ok I have seen the other thread about this, mine is 2 pvr-500's, and the fix listed doesn't work.

If I run sudo service mythtv-backend restart, everything works fine.  However, i put it in rc.local and that didn't fix it either.  the pid for mythbackend without rc.local is in the low 800's, but with rclocal in the 1.6k range, whereas when i restart after boot is in the 2.2k range.

I just really want this fixed without having to restart mythtv on every reboot.

---

### Post by ian dobson on 2010-07-29
Hi,

maybe try putting a sleep 5 infront of the restart command for myth-backend in your rc.local. Not a nice solution but if it works ......


Regards
Ian Dobson

---


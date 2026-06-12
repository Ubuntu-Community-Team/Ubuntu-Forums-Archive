---
title: "Mythtv- mythfilldatabase run from cron"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by ptipton on 2007-10-01
I am using Tvxb to grab program data based on the guide in the mythtv wiki. 
I have a scrip tvxb_grab that runs tvxb and then runs mythfilldatabase. If I run this script manually from the console then everything works fine, however if I run it as a daily cron job when I check the backend status after the job is complete it shows " mythfilldatabase started at ..... and is currently running    ... Warning is Mythfilldatabase running?". Any help much appreciated.

---

### Post by ptipton on 2007-11-13
bump

---

### Post by ptipton on 2007-11-15
Solved the problem by adding  "display=:0" at the start of the script, now works fine.

---


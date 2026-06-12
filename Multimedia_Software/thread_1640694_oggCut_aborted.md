---
title: "oggCut aborted"
date: 2010-12-08
forum: Multimedia Software
---

### Post by jomo-ub on 2010-12-08
I am trying to cut an ogg-file created by RecordItNow, by doing

oggCut -s 1000 -e -1 ~/Record-Now/aaradio-5.ogg ~/record-Now/test.ogg
  Starts running until
...
 6f 6d 37 fd 79 4b a7 cf e4 2e c9 38 9a b3 4b f5
 cb f9 71 26 ed d1 3c 02 57 ac 6e fb f5 f4 97 db
 eb 78 bb 65 d1 46 44 df 7a fa 24 e3 7e c1 63 5f
 88 21 df f3 e3 e1 a6 4e 7e 69 31 49 02 0f bf 9d
 5e 1c 69 d9 b5 db 3b 38 99 c1 f5 f3 a7 c2 4f 2f
Aborted

There is no clue to that "Aborted". Can anybody help?

I am runnung Ubuntu 10.10 with Kernel 2.6.35-23-generic-pae
and GNOME 2.32.0
on an AMD Athlon Dual 64X2 6000+ with 4GB memory
the oggCut is level 0.8.1 linstalled via Synaptic oggvideotools
disk-space = 360 iB

I searched for entries related to oggCut - but did not find any.
thanks  joe

---

### Post by FariAzz on 2012-05-11
I have the exact same issue with oggCut, I'm using Ubuntu 12.04.

Did you ever find a solution for this?

---

### Post by FariAzz on 2012-05-11
Well in case anyone runs into this same issue, what worked for me was to install oggz-tools and use oggz-chop that works in a similar way.

---


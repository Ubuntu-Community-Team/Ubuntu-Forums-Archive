---
title: "Unwanted Tuner Cards numbering etc.."
date: 2009-03-04
forum: Mythbuntu
---

### Post by rodercot on 2009-03-04
Hey Guys,

 I am wondering if there is a fix for this or should I even worry about it. 

 I have 3 tuners a pvr-150 and hvr-1250 in the master and then another pvr-150 in a slave and I will be installing another pvr-150 in the master for another source. 

 Through mistakes and trial and error with addition and removal of cards my numbering has gotten screwed up. IE

 on the master I have 

 tuner 3 master first card
 tuner 4 slave card but setup on master
 tuner 10 master dvb-t card. 

 Is there a way to reset these back to like 1, 2, 3 or should i even worry.
 
 thanks,

 Dave

---

### Post by crez79 on 2009-03-04
Solutions I know in descending crazyness
    1. A complete reinstall (very crazy)
    2. Manually edit database (just as crazy and will probably lead to #1)
    3. Let it be. (may drive you crazy, but to me it ain't worth it) The numbers don't have real meaning other than to document how many times it took to get your tuners set up. Mine numbers are up there... The encoder numbering resets itself and that is the more visible number so it at least doesn't rub it in your face too much...:P

---

### Post by klc5555 on 2009-03-05
> **crez79 said:**
> Solutions I know in descending crazyness
    1. A complete reinstall (very crazy)
    2. Manually edit database (just as crazy and will probably lead to #1)
    3. Let it be. (may drive you crazy, but to me it ain't worth it) The numbers don't have real meaning other than to document how many times it took to get your tuners set up. Mine numbers are up there... The encoder numbering resets itself and that is the more visible number so it at least doesn't rub it in your face too much...:P

Also 4. Backend setup --> delete all tuners on all backends; add tuners as though they were all new tuners. But definitely not something worth doing.

Cheers! :)

---


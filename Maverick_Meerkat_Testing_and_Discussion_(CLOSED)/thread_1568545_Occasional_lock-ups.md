---
title: "Occasional lock-ups"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-09-05
I have had two lock-ups with a fully updated install of 64 bit Maverick. It could be a coincidence but on both occasions I was using Firefox. Today I disabled ipv6 globally and Firefox is much more responsive. 

Could the lock-ups have been caused by ipv6?

---

### Post by oldsoundguy on 2010-09-05
Not sure, but FF has had some serious memory leaks off and on of late .. it appears, they fix it with an update, and then it comes back.  I have found that the best way is to shut down and re start the program.  (My machines are on 24/7/365 normally and only get shut down on a kernel update.)

---

### Post by exploder on 2010-09-05
Thanks for the reply. I guess I will have to just run the system and see if the problem has gone away. The system logs did not give me any clues as far as what the problem is.

---

### Post by exploder on 2010-09-05
Well, it just hard locked again.... Still hoping for a solution in the form of an update.

---

### Post by oldsoundguy on 2010-09-05
figure out what you have running and try it one program at a time .... also .. IF you are running ONLY FF and it happens, CHECK YOUR ADD ONS! 
You may want to disable all of them and then re-enable them one at a time. (this DOES happen!)

---

### Post by exploder on 2010-09-05
No add ons causing this unfortunately. I had this in Lucid, installing the NVidea drivers took care of this. I added the xswat repo, installed the latest NVidea drivers and installed Startup Manager to fix Plymouth.

I am keeping my fingers crossed and hoping this will take care of the problem.

---

### Post by 23meg on 2010-09-05
> **exploder said:**
> Well, it just hard locked again.... Still hoping for a solution in the form of an update.

Don't hope; do something to help fix it. That's what you're running Maverick for, right? Take a look at the following for a start:

[https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)
[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

---

### Post by exploder on 2010-09-05
Well, memtest confirmed that all my RAM is alright.

---

### Post by exploder on 2010-09-06
After installing the latest nvidea drivers yesterday from the x-swat repo the lock-up problem seems to be fixed! Today the newer drivers made it into the main repos. 

23meg, thanks for the advice and the wake up call.

---


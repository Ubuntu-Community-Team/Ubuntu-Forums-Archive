---
title: "MythTV, LIRC, and CommandIR"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by garcianc2003 on 2007-07-26
My apologies if I am not in the correct forum. This is my first post on this board.

I have got MythTV working and LIRC using a CommandIR mini USB IR transponder. The transponder has an IR emitter sending signals to a DirecTV RCA tuner model number RCR160SBM1.

Everything works... except I only have one slight problem. I can't get the computer to reliably change channels. Sometimes the tuner picks up only one digit or none at all. I even modified my channel change script to repeat the command three times (for debugging purposes) and still the same problem. I am also having the script echo the irsend command to a log, so I know that the right commands are going out. I have messed around enough with the location of the emitter to rule out a problem with its positioning.

I am grasping here but it looks to me like I have a poor signal. Is there some sort of intensity, frequency, or pulse duration parameter that I could change to improve performance?

Thanks in advance.
Nelson

---

### Post by garcianc2003 on 2007-07-27
Thanks anyway. I figured it out.

---

### Post by WhyWontThisWork on 2008-01-12
what was wrong?

---


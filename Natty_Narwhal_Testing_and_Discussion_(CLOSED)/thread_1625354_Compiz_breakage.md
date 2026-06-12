---
title: "Compiz breakage"
date: 2010-11-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by psusi on 2010-11-19
I didn't get to test natty last night, but tonight I tried and found windows did not have title bars.  I checked on IRC and heard others have experienced compiz breakage today and yesterday.  I checked .xsession-errors and it had compiz errors, and when I ran metaciy --replace, the title bars came back.

I hope this is known and will be fixed soon.  If it isn't in the next day or two, hopefully we can track the problem down here.

---

### Post by VMC on 2010-11-19
I've had compiz errors since day one on the ISO installs. A gdm restart brings back my panels.

I'm sure it has to do with the nvidia drivers. I haven't tried with proprietary drivers yet.

---

### Post by bdgdl08 on 2010-11-19
I was having trouble with this today... I just had to go to Appearance Settings and re-enable desktop effects and it was immediately resolved. Happened 3 times, but hasn't for a while now.

---

### Post by aytech on 2010-11-19
I have this problem from time to time on my laptop, metacity --replace or compiz --replace help most of the time, but sometimes when I close terminal after running the command, the desktop reloads and bars disappear again. Then I have to log out - log in again. 
Laptop has ATI graphics with proprietary driver enabled.

---

### Post by Starks on 2010-11-19
I hate when that happens.

It's like purgatory when neither Metacity nor Compiz is running.

---

### Post by dino99 on 2010-11-19
be aware on huge compiz changes next week (seen on planet)

---

### Post by karmila on 2010-11-19
I got this too with 2.6.37-3 and 2.6.37-5, some applet or even the panel crashed on start up but 2.6.37-2 more stable though.

---


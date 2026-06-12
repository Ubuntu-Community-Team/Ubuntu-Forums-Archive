---
title: "Question about PPA?"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2011-01-23
What if I am using a 10.10 PPA and then upgrade to 11.04. Would I have to purge the data and then use a 11.04 PPA of the same application to receive updates?

Also, I am aware 11.04 is in ALPHA. I usually test early and keep updating from there. So far so good.

---

### Post by dino99 on 2011-01-23
Most of the time a 10.10 ppa can work on 11.04 (its often the case because there is no choice for 11.04 ppa anyway), but sometime there is some dependecies conflicts that need to use a 11.04 ppa (if it exist) or to remove the 10.10 one. So you might know that using ppa (especially those of non regular dev maintainer) are "at your own risk" and need all your attention.

---

### Post by Starks on 2011-01-23
Usually it should be sufficient to change "maverick" to "natty" in the Software Sources for the PPA entry.

---


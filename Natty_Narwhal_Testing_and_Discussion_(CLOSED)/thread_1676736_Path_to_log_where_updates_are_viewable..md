---
title: "Path to log where updates are viewable."
date: 2011-01-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2011-01-27
What is the path to the daily logs of updates that I have downloaded from mirror?

---

### Post by mc4man on 2011-01-27
Most likely /var/log/dpkg.log
(you could probably grep upgrade to willow out excessive lines, maybe like this among several ways
grep upgrade /var/log/dpkg.log

(I remember there is a way to do multiple words, but as usual forget (to get just date and upgrade

maybe like this (others know much better than me. I just T&E
grep 01-27 /var/log/dpkg.log |grep upgrade

---

### Post by garvinrick4 on 2011-01-27
Thank You mc4man:

---


---
title: "zombie processes in Mythbuntu"
date: 2015-09-26
forum: Mythbuntu
---

### Post by linuxhippy on 2015-09-26
Hi-I have mythbuntu 14.04.3 installed and just noticed from top that I have 2 zombie processes.  ps aux gives this:

root     28191  0.0  0.0      0     0 ?        Z    13:44   0:00 [apport-gtk] <defunct>
root     28197  0.0  0.0      0     0 ?        Z    13:44   0:00 [apport-gtk] <defunct>

How do I kill these?  I used sudo kill -9 28191 but that didn't work.

---


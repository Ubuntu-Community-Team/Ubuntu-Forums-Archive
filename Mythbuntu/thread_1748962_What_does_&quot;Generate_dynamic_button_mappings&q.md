---
title: "What does &quot;Generate dynamic button mappings&quot; do ?"
date: 2011-05-04
forum: Mythbuntu
---

### Post by declanmullen on 2011-05-04
Within Mythbuntu Control Centre's Infrared section, what does ticking the "Generate dynamic button mappings" option do ?

I've been looking through the Mythbuntu documentation and there doesn't seem to be an explanation. Is there any doco on the subject ?

Thanks,
Declan

---

### Post by Dan_R on 2011-05-04
From what I understood, it generates key presses corresponding with what you hit on your remote. For example the 0-9 numbers generate 0-9 as if on a keyboard, the back button becomes ESC etc. Reading your other thread it may be the last step on getting your remote working. I believe what is generated is a file called, without quotes, "lircrc". The file will likely be located in /home/username/.mythtv/ if you wanted to peek at it. Please note the key presses are custom just for mythtv.

---

### Post by declanmullen on 2011-05-04
many thanks.

---

### Post by superm1 on 2011-05-04
Yes, it does this using mythbuntu-lircrc-generator.  You can read the --help and man page to see what else it supports.

---

### Post by declanmullen on 2011-05-04
Many thanks.
It's all clear now.

---


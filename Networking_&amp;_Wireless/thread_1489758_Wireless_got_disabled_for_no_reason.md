---
title: "Wireless got disabled for no reason"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by Denverite on 2010-05-21
I installed ubuntu 10.04 on dell vostro 1500. It all worked fine for 2 days, but for no reason the wireless got disabled with no change in the sys settings. I wonder how to enable the wireless and fix this problem.

Thanks.

---

### Post by TheGnomeOfMetal on 2010-05-21
right click the network manager applet in the system notification area. click Enable Wireless.

---

### Post by Denverite on 2010-05-21
The "enable wireless" checkbox is unchecked and disabled, which means i cannot change it. Is there any other way i could enable the wireless network?
 
p.s thanks though for the suggestion.

---

### Post by Iowan on 2010-05-21
See if the interface shows up under **ifconfig -a** (probably won't) - or **sudo lshw -C network** (hopefully will)...

---

### Post by soulchaos0 on 2010-05-21
I'm having the same problem...i typed in what it said, and i can't make heads or tails of what came up...

---

### Post by Denverite on 2010-05-22
Yup, I got it.

Thanks a lot guys.

---

### Post by Iowan on 2010-05-22
> **Denverite said:**
> Yup, I got it.What did you find - what fixed it?
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by Denverite on 2010-05-22
right click on notification area, check the wireless network to enable it.
thats it!

---


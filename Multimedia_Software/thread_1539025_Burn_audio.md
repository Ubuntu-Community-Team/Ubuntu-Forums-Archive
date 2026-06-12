---
title: "Burn audio"
date: 2010-07-26
forum: Multimedia Software
---

### Post by GRobi829 on 2010-07-26
New to linux, i have my music on my hard drive but im having trouble burning files to CD-R discs, the CD/DVD creator acts like its burning but then the cds wont play

---

### Post by sikander3786 on 2010-07-26
Hi.

Which CD Burning Software are you using? Is the CD-RW in good shape? Are you trying to create an Audio CD (playable on most music systems) or a Data CD (playable on computers and some mp3 players)?

---

### Post by lidex on 2010-07-26
I believe that's a front end for Brasero?
Try xfburn - it's in the repos:
```
sudo apt-get install xfburn
```

Open the program from the Sound & Video menu. You'll see four buttons in the lower section. Press the one that says "Audio CD". You can now add files to the bottom pane and it should convert them for you on the fly.

---


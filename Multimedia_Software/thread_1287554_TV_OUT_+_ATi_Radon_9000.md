---
title: "TV OUT + ATi Radon 9000"
date: 2009-10-10
forum: Multimedia Software
---

### Post by shadowClint on 2009-10-10
Dear forums,

I have a pretty old ATi Radeon 9000 graphics card, and I'd like to connect it to the TV, so I can watch videos, play, etc. on my TV screen. I connected my video card to the TV through an S-Video cable, which goes into a video, and the video si connected to the TV itself.

Since its an older card, the newer, fglrx drivers won't support it (as the Ubuntu HowTo said so), so I can't rely on those (unfortunately I tried, and messed-up brutally, but I managed to recover)

I tried atitvout, but it doesnt seem to detect my TV screen, so I feel I am missing something, but I didn't find a simple up-to-date method to achieve my goal.

Thank you for your help,

---

### Post by Thelasko on 2009-11-25
Atitvout probably does support your card.  You have to play with the commands a little.  Try
```
sudo atitvout -f t
```
or
```
sudo atitvout -r t
```

---


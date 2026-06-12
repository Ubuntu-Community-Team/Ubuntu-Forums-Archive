---
title: "Leadtek Winfast TV2000 XP RM Video Problems"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by davem2312 on 2007-09-17
I just purchased a Leadtek Winfast TV2000 XP RM, and am trying to install it on my ubuntu box.  I am running kernel version 2.6.22-11 Gutsy, and have a small video problem.

After doing this...

```

rmmod bt878
rmmod tuner
rmmod bttv
modprobe bttv card=34 tuner=43

```

I get reception, and great audio.  The problem comes with the video.  The images are black and white, and flicker quite a bit, and are a little out of align, sort of like the signal quality is bad from an antenna or something.  I have tried it out one Windows, so I know that it is not a card issue.  Is there any advice anyone can give me?  I will be happy to post more of my system specs and configurations if asked.  Thank you.

---

### Post by davem2312 on 2007-09-19
So turns out, I installed Feisty, and it works perfectly in feisty... so is this perhaps related to Gutsy?  I'm asking if I should file a bug report...

---

### Post by damyrade on 2007-09-20
nvm

---


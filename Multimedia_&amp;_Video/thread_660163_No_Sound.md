---
title: "No Sound"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by mlwgszgao on 2008-01-06
Hey, I'm sort of new to Ubuntu so I'm not sure if this is a simple matter or hopeless

I have a Dell Dimension 8400 Desktop which I installed Feisty and then upgraded to Gutsy on.  Now, I'm getting no sound from my speakers and I tried several ways for fixing this with no result.  It seems none of the ways that I've searched works so far.  So please someone help me get my sound back!

---

### Post by icheyne on 2008-01-06
Good luck

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Yellow Pasque on 2008-01-06
That model came with a few different sound options. What card/chip are you running? If unsure, post output of lspci:
```
sudo update-pciids
sudo lspci
```

---

### Post by mlwgszgao on 2008-01-06
I don't know why, but when I restarted my computer, the sound was back.  Thanks for all your help guys!

---


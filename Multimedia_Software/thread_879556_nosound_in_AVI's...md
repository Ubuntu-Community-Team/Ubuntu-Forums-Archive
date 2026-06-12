---
title: "nosound in AVI's.."
date: 2008-08-04
forum: Multimedia Software
---

### Post by Disrupt on 2008-08-04
Hello, I'm having trouble playing AVI's, the picture comes up just find but they have no sound, ive tried them in VLC and mplayer and neither work, any suggestions?

---

### Post by trevelyan on 2008-08-04
this has happened to me a few times with some movies.. i found that dragon player can play the sound.

also you could try typing this in a terminal in case the problem is that another application has a hold on your sound card
```
sudo killall pulseaudio
```

---

### Post by Disrupt on 2008-08-04
the sudo killall thing worked, thanks alot :)

---


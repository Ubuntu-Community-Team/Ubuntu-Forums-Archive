---
title: "Microphone always active"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by greenbakk on 2007-02-18
After some problems I've finally managed to get working microphone input on Audigy 4 sound card. However there are still some issues like:
- mic level control button is randomly moving and thus changing input level
- it looks that mic input is always on, even when no program uses sound device

I would like microphone not to active when sound card is not used by any program - like skype for example. 

Thanks for any hint

---

### Post by thingy on 2007-02-18
use the alsamixer program to setup your mixer settings as you want(i.e. disable mic) and ensure that they got saved by "sudo alsactl store 0"

---


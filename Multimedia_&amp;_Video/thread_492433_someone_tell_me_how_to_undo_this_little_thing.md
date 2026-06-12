---
title: "someone tell me how to undo this little thing"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by ninjapig on 2007-07-04
i did this after reading someone's advice to install frontend gmplayer


sudo rm /usr/bin/gmplayer
sudo ln -s /usr/bin/mplayer32 /usr/bin/gmplayer


no idea on how to undo this and my only good mediaplayer: mplayer won't start up now.


first one to answer wins.


please :)

---

### Post by johnc4510 on 2007-07-04
Try reinstalling mplayer

sudo apt-get install mplayer

---

### Post by ninjapig on 2007-07-04
nope it says too many child process

---

### Post by johnc4510 on 2007-07-04
try removing mplayer and then reinstalling

sudo apt-get --purge remove mplayer

sudo apt-get install mplayer

---

### Post by ninjapig on 2007-07-04
Thanks!

That did it!

I'm usually scared of unisntalling and installing things in ubuntu.

---

### Post by johnc4510 on 2007-07-04
Some things are problematic in that respect, but you will learn which as you go along. Just a new learning curve is all.
 
Good Luck

---


---
title: "Media Player Now Plays DVD But No Video"
date: 2010-03-07
forum: Multimedia Software
---

### Post by sylar petrelli on 2010-03-07
Hello,

I was setting up my Totem Movie Player on Ubuntu 9.10 and at first it wouldn't play dvds at all. So, I went online and entered these two commands into the terminal to play restricted dvds.

sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh

DVDs will now play on Totem, but now I don't have any video. I can hear sound and if click around the screen I can get it to play but I still don't have any video.

Thinking it might be exclusive to Totem. I tried to use VLC media player. Same thing.

I also tried both dvd drives on my computer and tried different DVDs. Still same thing.

Thanks for the help,
SP

---

### Post by ChildOfMana on 2010-03-07
I'm not sure if this will work or not but give it a try:

```
sudo apt-get install totem-xine libxine1-ffmpeg
```

---

### Post by sylar petrelli on 2010-03-08
I tried what you said above and it still didn't work. Thanks for the information. Anything else I can try?

---

### Post by ChildOfMana on 2010-03-08
I'm all out of suggestions I'm afraid. Sorry amigo :(

---

### Post by pyromidget on 2010-10-25
Hi all, apologies for the thread necromancy but i'm having the exact same problem with my dad's laptop.  if i remember correctly its got a unichrome s3 graphics processor, if that makes any difference...

Anyone got any suggestions i can try?

---


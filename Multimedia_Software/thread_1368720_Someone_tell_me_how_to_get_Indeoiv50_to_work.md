---
title: "Someone tell me how to get Indeo/iv50 to work?"
date: 2009-12-31
forum: Multimedia Software
---

### Post by gavinfoxx on 2009-12-31
Okay, so I have TRIED to read and figure out how to do this...

but can someone tell me precisely WHAT I need to type into the terminal in order to get an indeo / iv50 .avi file to play? I am running 32 bit Karmic, and I have NO idea what I am doing. Some monkey see monkey do instructions would be GREAT!

---

### Post by mc4man on 2009-12-31
You need either mplayer or a xine based player (kaffeine, xine, a working totem-xine) and w32codecs.

for mplayer you could also add a frontend such as smplayer or gnome mplayer.

for w32codecs either just go [here]("http://packages.medibuntu.org/karmic/w32codecs.html") and dl and install directly or run this to add the repo to your sources

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

If you added medibuntu then run this
```
sudo apt-get install w32codecs
```

For players install your choice or this should do (both frontends

```
sudo apt-get install mplayer smplayer gnome-mplayer
```

---


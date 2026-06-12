---
title: "ubuntu 9.04 totem cannot play dvd"
date: 2009-10-25
forum: Multimedia Software
---

### Post by rikitiki on 2009-10-25
hi installed ubuntu 9.04 jaunty
tried to watch the dvd, totem has problems... says nothing closes automatically...
anyone knows the reason? thanks...

---

### Post by vinutux on 2009-10-25
Install  ubuntu-restricted-extras first

in terminal | Applications > Accessories > Terminal

```
sudo apt-get install  ubuntu-restricted-extras
```

then add **[mediubuntu repos]("http://www.medibuntu.org/")** and install libdvdcss2 

Read help here [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by johnzollo on 2009-10-25
Ahhh... free DVD in Linux may be illegal in the country you're in.  It'll probably work, but... WATCH YOUR BACK!!!!!

I heard Fluendo has a DVD player and Power DVD sells one through the canonical store, but they cost $$$

Quite a conundrum huh?

Thank someone for spell checking!

-John

---

### Post by rikitiki on 2009-10-25
hi vinutux,

sorry i forgot to mention...

i have already installed all what you have suggested, including the medibuntu, thanks!

any other suggestions?

---

### Post by kixome on 2009-10-25
libdvdcss2.deb search fot it and install it, will play dvd's. also you may want to edit your menus to used movie player-gstreamer, and for the best dvd playback # sudo apt-get install vlc

and use vlc. actually with this package installed you can just drag and drop the dvd files off the dvd and drag them to another to copy(if both are the same type of dvd (for example- dvd9 dual layer vs dvd5 single layer)

---

### Post by rikitiki on 2009-10-25
thanks kixome,

installed vlc, now it plays it but there is no sound...

do you have any ideas why i have no sound...
i am using ubuntu9.04 jaunty...

thanks in advance!

---

### Post by vinutux on 2009-10-25
right click file properites audio/vidoe tab check what type of codec on it ............

---

### Post by kixome on 2009-10-25
also open your mixer(the volume icon) go to edit / preferences and make sure all options are checked, turn up master/lfe/surround/center/side/cd/ and basically eveything but the input/capture stuff if that doesn't work try restarting, and if that doesn't work I am at a loss. also k9copy is the best trancoder for dvd's

---

### Post by rikitiki on 2009-10-25
sorry vinutux,

can you tell me how and where to do that?

is file properties of dvd or what?

sorry kixome, can you tell me step by step? i am not yet used to ubuntu environment...

i only installed it today... sorry.

---

### Post by kixome on 2009-10-25
never pay for software- unless you are a commercial entity!

---

### Post by rikitiki on 2009-10-25
i don't know if this helps to solve the problem...

the other post i have posted was that 
i can play youtube videos, but i have no sound...

---

### Post by vinutux on 2009-10-25
> **rikitiki said:**
> sorry vinutux,

can you tell me how and where to do that?

is file properties of dvd or what?

sorry kixome, can you tell me step by step? i am not yet used to ubuntu environment...

i only installed it today... sorry.

sorry i thought its is a video file............

---


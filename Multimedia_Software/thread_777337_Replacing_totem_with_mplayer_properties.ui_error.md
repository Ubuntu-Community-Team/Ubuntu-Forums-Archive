---
title: "Replacing totem with mplayer properties.ui error"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Pitou on 2008-05-01
Hello,

I'm trying to use mplayer instead of totem for all my multimedia files.

I did remove totem using synaptic and installed mplayer.

Now I can play movie files perfectly with mplayer by double clicking it, but if I do a right click --> Properties --> Audio/Video, I get this error:

"Couldn't load the '/usr/share/totem/properties.ui' interface. Failed to open file '/usr/share/totem/properties.ui': No such file or directory"

Is it possible to tell ubuntu to use mplayer for this?

Thank you.

Pitou!

---

### Post by Pitou on 2008-05-01
bump.

---

### Post by sandervdv on 2008-05-14
hi,

I managed a workaround for this problem:

install the "totem-common" package in synaptic

If you don't like this (for any reason) you can do the following:

make a backup of "/usr/share/totem/properties.ui", 

```
cp /usr/share/totem/properties.ui ./Desktop
```

In Synaptic remove all the totem packages (except plparser10) 

and placed the file in an empty "/usr/share/totem/"

```
sudo mkdir /usr/share/totem
```
```
sudo cp ./Desktop/properties.ui /usr/share/totem
```

worked for me

---

### Post by sandervdv on 2008-05-14
i noticed that when you restart the audio/video tab is gone, so the problem also should be gone.

---

### Post by masque7 on 2010-07-09
This works but if you want right-click an audio or video file and go to *Properties* then you will face the error message again.

Removing totem is a pain.

---


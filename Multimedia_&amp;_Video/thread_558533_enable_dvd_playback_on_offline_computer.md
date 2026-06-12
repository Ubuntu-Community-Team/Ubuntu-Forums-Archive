---
title: "enable dvd playback on offline computer"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by AlmaTlust on 2007-09-24
A friend of mine wants to use his old computer for watching dvds. I installed Xubuntu Feisty on his machine - works fine. Installed libdvdcss. Inserted dvd - gxine startx up, and gives error message "no demultiplexer found".
How can I make this work? His computer is offline, so I have to download everything from my computer, burn it on cd and give it to him. Would install vlc or totem or mplayer help?

---

### Post by stoodleysnow on 2007-09-24
Try totem with the xine backend.:)

---

### Post by AlmaTlust on 2007-09-25
how do I figure out what dependencies totem has? Remember, I have to download all the debs manually as the other computer is offline...

---

### Post by RomeReactor on 2007-09-25
Hi. I don't know if Xubuntu has Synaptic, but if it does, search for:

* totem-xine
* libxine1
* libxine1-ffmpeg
* libxine-extracodecs

And mark them for installation; then (still in Synaptic) go to "File->Generate package download script". Now copy that script to your machine, run it, and copy the downloaded packages to your friend's system. Once there, open Synaptic again, and go to "File->Add downloaded packages".

---

### Post by the8thstar on 2007-10-17
there's no such thing as libxine-extracodecs

---


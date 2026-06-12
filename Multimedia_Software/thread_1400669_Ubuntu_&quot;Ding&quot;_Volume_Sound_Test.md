---
title: "Ubuntu &quot;Ding&quot; Volume Sound Test"
date: 2010-02-07
forum: Multimedia Software
---

### Post by gcs1984 on 2010-02-07
In Windows XP, Vista and so forth, whenever the volume is adjusted at the bottom right-hand corner of the screen, there is a "ding" noise played to give the user an idea of the volume level they have just set. This is a rather convenient feature, because it prevents for example someone from starting a movie or a song with the volume turned up too loud. Unfortunately, as far as I can see there is no such feature on Ubuntu. What can I do to get (or at least substitute) this feature?

Thanks a lot,

gcs1984

---

### Post by Joe of loath on 2010-02-07
I've also wondered about this. I know fedora has it, and fedora uses gnome and pulseaudio like ubuntu.

---

### Post by Yellow Pasque on 2010-02-07
Add a custom application launcher to your panel that uses the command:
```
canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg
```

---


---
title: "watching a dvd iso w/o mounting?"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by bottlekeynut on 2007-01-04
hey,

i have this dvd iso i'm trying to view, and i'm wondering if there's a way i can do so without mounting it? i realize i could mount it, but it seems like i should be able to watch this without having to do anything as root, so if there's another way, i'd like to use that.

i tried opening the iso in vlc, and the results can be best described as "screwy". plays one of the intro screens, then dies after that.

i realize i'm new, i tried doing a brief search to see if this topic's been addressed already and was unable to find anything. if this has been brought up before, i apologize in advance

thanks

---

### Post by taurus on 2007-01-04
Applications -> Accessories -> Terminal
```
gmplayer **filename.iso**
```

---

### Post by bottlekeynut on 2007-01-05
i couldnt find gmplayer in aptitude, but i tried opening the iso in totem and that seemed to do the trick.

---

### Post by kd7swh on 2007-01-05
These work,

```
vlc  filename.iso
```

```
gmplayer  filename.iso
```

mplayer packages need to be installed for gmplayer to work

vlc packages need to be installed for vlc to work.

---


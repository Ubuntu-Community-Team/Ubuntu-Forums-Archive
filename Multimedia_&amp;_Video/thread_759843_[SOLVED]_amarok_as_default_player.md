---
title: "[SOLVED] amarok as default player"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by elidoperezmd on 2008-04-19
easy question, how can i make amarok the main music player, by this i mean default player. thanks for the replies

---

### Post by mc4man on 2008-04-19
If by default you mean pop in a cd and have amarok start and play -  then in preferences> removable drives and media> multimedia paste this in box for cds
```
amarok -cdplay %d
```
i'm not sure if you need cdplay installed (package cdtools ) I installed it to read man page

note; it does take amarok several sec's to read cd and load playlist

---

### Post by elidoperezmd on 2008-04-19
What im talking is that if i want to play an mp3, and i double click it, i want to play it with amarok. But it opens with another software.

---

### Post by mc4man on 2008-04-20
That's  very simple - right click on an mp3 and if amarok isn't listed under open with add it. Then again right click on mp3 >properties> open with> and double click amarok to set as default for mp3's.

---


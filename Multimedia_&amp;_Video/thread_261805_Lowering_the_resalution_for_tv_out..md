---
title: "Lowering the resalution for tv out."
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by morikaweb on 2006-09-20
So far the only way I can figure to get tv out working with my ati x700 card is to use clone mode. So what I want to know is if I change my laptop resolution to 640*480 for tv out can I damage my LCD? Also is it possible to have the tv run at a different rez than the lcd?

---

### Post by morikaweb on 2006-09-21
?

---

### Post by jkwarras on 2006-09-21
Yes you can. Just look at the '/etc/X11/xorg.conf' file, and look for the TV-out screen and change the resolution mode there.

---

### Post by morikaweb on 2006-09-21
for starters my xorg didnt have a tv section and I still had tv out. But to try your advice I made a tv screen tv device and tv monitor section and it still sets the tv to 1680x1050.

---

### Post by jkwarras on 2006-09-22
Check in the preferences>screen resolution. You should see two sections, one for each scrren. You could try to change there the tv-out screen.

If you can't try this:
```
sudo aticonfig --initial=dual-head
```

or directly 

```
sudo aticonfig --dtop=clone
```

See if the sections are correctly created, then you could try to add the tv-out screen resolution you'll like to get and change it from the preferences>screen resolution.

Hope it helps.

---


---
title: "dvd"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by geordie chris on 2007-03-22
i want to play a dvd .totem says i dont have the right plugins . i went to the repository dowmloaded the plugin, but still nothing .what am i doing wrong

---

### Post by taurus on 2007-03-22
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by floke on 2007-03-22
way-yi man, ya need the dvdcss2 plugin, which unfortunately is licensed and so not included! You could: (a) Go get it here [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/) - usual disclaimers on 3P repos etc.; and/or (b) Get VLC (Totem is pants anyway) - sudo apt-get vlc

Hope this helps

---

### Post by geordie chris on 2007-03-22
in sudo it will not let me get vlc

---

### Post by floke on 2007-03-22
Have you enabled multiverse and universe in your software sources?
It's in the repositories so you should be able to pull it no probs.

---

### Post by kotty1216 on 2007-04-01
If you copied exactly what steve said it won't work because, he put down

```
sudo apt-get vlc
```

He forgot to put install in it. So you should try it again with,

```
sudo apt-get install vlc
```

if you haven't already. I did this and it works great.

---


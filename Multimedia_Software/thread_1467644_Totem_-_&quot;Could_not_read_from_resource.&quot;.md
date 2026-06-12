---
title: "Totem - &quot;Could not read from resource.&quot;"
date: 2010-04-30
forum: Multimedia Software
---

### Post by kaldor on 2010-04-30
Ubuntu 10.04 with proprietary nvidia drivers enabled. Ubuntu restricted extras also installed.

Can't play DVDs on Ubuntu. Totem gives the "Could not read from resource." when trying to load a DVD. VLC won't load it either.

Any packages I am missing? The movie is Pirates of the Caribbean if that matters at all.

---

### Post by mc4man on 2010-04-30
Maybe you don't have libdvdcss2 installed, if not then  running this in a terminal will install it for you

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If you're not happy with totem's dvd playback abilities then try vlc

```
sudo apt-get install vlc
```

---

### Post by illgetit on 2011-11-09
I know this is an old thread, but it's still relevant. Thanks for posting this info

---

### Post by yogeshthegenius on 2012-10-07
Thanks a lot!!!

---

### Post by nothingspecial on 2012-10-07
Old thread.

Closed.

---


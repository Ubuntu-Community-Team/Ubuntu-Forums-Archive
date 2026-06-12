---
title: "multimedia dvd"
date: 2010-03-27
forum: Multimedia Software
---

### Post by mrpacman on 2010-03-27
Have 9.10 instaled with dvd software as ubuntu software for playing dvd's but it comes up with NEED uri handler for DVD.

---

### Post by mc4man on 2010-03-27
run these 2 commands in a terminal

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly 
```
```

sudo /usr/share/doc/libdvdread4/install-css.sh
```

The default totem player may or may not suit you as a dvd video player, if not

```
sudo apt-get install vlc
```

(there are some ppa's for improved gstreamer plugins and a more up to date vlc if desired.

---


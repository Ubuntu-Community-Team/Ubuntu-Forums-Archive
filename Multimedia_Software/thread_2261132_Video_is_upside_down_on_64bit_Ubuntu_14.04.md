---
title: "Video is upside down on 64bit Ubuntu 14.04"
date: 2015-01-16
forum: Multimedia Software
---

### Post by frenchpark43 on 2015-01-16
Just after installation my Video is upside down on 64bit Ubuntu 14.04 on MPlayer and VLC . Video on Chrome and Firefox are OK. Otherwise video plays well

---

### Post by mc4man on 2015-01-16
Seems a bit odd for a new install. What happens if you do this, then open vlc & play a video
```
mv ~/.config/vlc/vlcrc ~/.config/vlc/vlcrc.bak
```

---

### Post by frenchpark43 on 2015-01-21
That fixed it. Thanks.

---

